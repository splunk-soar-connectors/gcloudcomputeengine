[comment]: # "Auto-generated SOAR connector documentation"
# Google Cloud Compute Engine

Publisher: Splunk Community  
Connector Version: 1\.0\.3  
Product Vendor: Google  
Product Name: Compute Engine  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.1\.0  

This app integrates with google cloud compute engine API that supports investigative and generic actions

[comment]: # " File: README.md"
[comment]: # ""
[comment]: # "  Copyright (c) 2021-2022 Splunk Inc."
[comment]: # ""
[comment]: # "  Licensed under the Apache License, Version 2.0 (the 'License');"
[comment]: # "  you may not use this file except in compliance with the License."
[comment]: # "  You may obtain a copy of the License at"
[comment]: # ""
[comment]: # "      http://www.apache.org/licenses/LICENSE-2.0"
[comment]: # ""
[comment]: # "  Unless required by applicable law or agreed to in writing, software distributed under"
[comment]: # "  the License is distributed on an 'AS IS' BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,"
[comment]: # "  either express or implied. See the License for the specific language governing permissions"
[comment]: # "  and limitations under the License."
[comment]: # ""
Actions in this app utilize the following API:
https://cloud.google.com/compute/docs/reference/rest/v1

## Explanation of Asset Configuration Parameters

The asset configuration parameters affect \[test connectivity\] and all the other actions of the
application. Below are the explanation and usage of all those parameters.

-   **Contents of Service Account JSON file -** After creating a Service Account for authenticating
    with Google Cloud Storage (https://console.cloud.google.com/iam-admin/serviceaccounts/project),
    the file can be downloaded. Paste the contents into the asset configuration input as-is.
-   **Project ID -** The Google Cloud Project ID.


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Compute Engine asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**key\_json** |  required  | password | Contents of Service Account JSON file
**project** |  required  | string | Project ID

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[tag instance](#action-tag-instance) - Modify tags on instance  
[describe instance](#action-describe-instance) - Get instance information  
[stop instance](#action-stop-instance) - Stops an instance  
[start instance](#action-start-instance) - Starts an instance that was previously stopped  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'tag instance'
Modify tags on instance

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**zone** |  required  | Zone of the instance | string |  `gcloud computeengine zone` 
**id** |  required  | ID of the instance | string |  `gcloud computeengine id` 
**tags** |  required  | Network tags to apply to the instance\. Will overwrite existing tags | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.zone | string |  `gcloud computeengine zone` 
action\_result\.parameter\.id | string |  `gcloud computeengine id` 
action\_result\.parameter\.tags | string | 
action\_result\.data | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'describe instance'
Get instance information

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**zone** |  required  | Zone of the instance | string |  `gcloud computeengine zone` 
**id** |  required  | ID of the instance | string |  `gcloud computeengine id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.zone | string |  `gcloud computeengine zone` 
action\_result\.parameter\.id | string |  `gcloud computeengine id` 
action\_result\.data\.\*\.machineType | string | 
action\_result\.data\.\*\.cpuPlatform | string | 
action\_result\.data\.\*\.id | string | 
action\_result\.data\.\*\.status | string | 
action\_result\.data\.\*\.canIpForward | boolean | 
action\_result\.data\.\*\.creationTimestamp | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary\.id | string | 
action\_result\.summary\.name | string | 
action\_result\.summary\.machineType | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'stop instance'
Stops an instance

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**zone** |  required  | Zone of the instance | string |  `gcloud computeengine zone` 
**id** |  required  | ID of the instance | string |  `gcloud computeengine id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.zone | string |  `gcloud computeengine zone` 
action\_result\.parameter\.id | string |  `gcloud computeengine id` 
action\_result\.data\.\*\.status | string | 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.zone | string | 
action\_result\.data\.\*\.targetId | string | 
action\_result\.data\.\*\.startTime | string | 
action\_result\.data\.\*\.endTime | string | 
action\_result\.data\.\*\.operationType | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'start instance'
Starts an instance that was previously stopped

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**zone** |  required  | Zone of the instance | string |  `gcloud computeengine zone` 
**id** |  required  | ID of the instance | string |  `gcloud computeengine id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.zone | string |  `gcloud computeengine zone` 
action\_result\.parameter\.id | string |  `gcloud computeengine id` 
action\_result\.data\.\*\.status | string | 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.zone | string | 
action\_result\.data\.\*\.targetId | string | 
action\_result\.data\.\*\.startTime | string | 
action\_result\.data\.\*\.endTime | string | 
action\_result\.data\.\*\.operationType | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 