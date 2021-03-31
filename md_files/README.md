# Building Energy Modeling API

<img src="https://raw.githubusercontent.com/SE-Analytics-Team/public-images/master/bem_api/content.png" style="zoom:67%;" />

---

# Overview

## Overview and usage

This document explains the usage of the `Building Energy Modeling` API.

This API automatically identifies the best thermal model for a building, a plant in order to assess energy savings, to detect abnormal energy consumption.

The typical use cases of the API are :

1. build a baseline model of a building using the “thermal signature” models recommended by **ASHRAE** and **IPMVP**,
2. build a target model using the same mechanism (assuming the user has created simulated target data)
3. follow-up the baseline and target models of a building – in particular to detect faults and to compute savings

The **thermal signature** of a building describes the energy consumption of a building considering external temperature. Basically it models how much energy a building will require for heating when external temperature is cold (heating degree days, **HDD**) and how much energy it will require for cooling when external temperature is hot (cooling degree days, **CDD**).

The **heating change point** is the outside air temperature below which the heating system is on.
The **cooling change point** is the outside air temperature above which cooling system is on.

There are five basic types of change point models according to ASHRAE guideline 14, appendix D4 (2 parameters, 3 parameters (heating), 3 parameters (cooling), 4 parameters, 5 parameters).

This document provides a general tutorial for users who want to consume the Building Energy Modeling API.

## Features

The Building Energy Modeling API includes 4 features:

- Create a building energy model (thermal signature of the building) from a dataset containing several drivers  (e.g. external temperature) and an energy consumption measure (*createModel* endpoint).

- Apply a previously generated model over a new dataset to forecast the energy consumption out of the provided drivers (*applyModel* endpoint).

- Get metrics telling if a model is good enough to compute savings (*assessModelQualityForSavings* endpoint).

- Get information on an existing model (*getModelInformation* endpoint).

## How it works

<img src="https://raw.githubusercontent.com/SE-Analytics-Team/public-images/master/bem_api/BEM_Principles.jpg" style="zoom:67%;" />

## Hands-on application

Take the tour and experiment on your own data prior to any development through our hands-on application !

https://try-analytics-se.azurewebsites.net/bem

<img src="https://raw.githubusercontent.com/SE-Analytics-Team/public-images/master/bem_api/MicroApp.png" style="zoom:67%;" />



## Limitations

Amount of calls to the API in the SANDBOX are limited.

To get a full experience and extend the thresholds, please subscribe to the API and use the production environment.


## Getting Started 

### Run in Postman collection

First, you need to download the free [Postman application](https://www.google.com) for your operating system. Postman currently supports Mac, Windows, and Linux. Once you have Postman installed, you can import the BEM API Postman collection by clicking the orange “Run in Postman” button. At this point, you should see the Forecasting API folder in the left-hand column under the Collections tab.

<a href="https://github.com/sieiieowoer/jens/blob/master/forecasting_nominalErrors.postman_collection.json" target="_blank"><img src="https://run.pstmn.io/button.svg" alt="Run forecasting in Postman"></a>



<!--TO BE VALIDATED BY AAI : only for APIs who don't have any micro-application ?-->

### Step 1: Setup environment

### Step 2: Prepare Data

### Step 3: Create a new energy model

### Step 4: Train model 

### Step 5: Apply an existing forecasting model to new data

### Step 6: Get model information on an existing prediction model

## Authentication guide

This API uses API keys to authenticate and allow access to the API.

Your API keys carry many privileges, so be sure to keep them secure!

The API key should be included in all API requests in the Authorization header that looks like the following:

| **Authorization**     | your_subscription_key     |

For steps on how to generate your_subscription_key please refer to the Features tab.

## Response Codes

We follow the error response format proposed in [RFC 7807](https://tools.ietf.org/html/rfc7807)also known as Problem Details for HTTP APIs.  As with our normal API responses, your client must be prepared to gracefully handle additional members of the response.

### Unauthorized

<RedocResponse pointer={"#/components/responses/Unauthorized"} />

### AccessForbidden

<RedocResponse pointer={"#/components/responses/AccessForbidden"} />


### 400

BadRequest
Your request could not be processed.
This is a generic error.
InvalidAction
The action requested was not valid for this resource.
This error is returned when you try to access an action that doesn't exist. For example, /campaigns/{id}/actions/send.
InvalidResource
The resource submitted could not be validated.
For field-specific details, see field_warnings or field_errors objects. This error means that the object submitted to a POST or PATCH request failed to validate against JSON schema, and could relate to campaign, interest group, merge field, or any other available object.
JSONParseError
We encountered an unspecified JSON parsing error.
This error means that your JSON was formatted incorrectly or was considered invalid or incomplete.

### 401

APIKeyMissing
Your request did not include an API key.
This error suggests that your API key was missing from your request, or that something was formatted or named improperly in your header. To learn more, check out Get Started with the Mailchimp API.
APIKeyInvalid
Your API key may be invalid, or you've attempted to access the wrong data center.
Check that your API key was input correctly, and verify which data center to access. To learn more, check out Get Started with the Mailchimp API.

### 403

Forbidden
You are not permitted to access this resource.
This is a generic error.
UserDisabled
This account has been disabled.
The Mailchimp account is deactivated. Contact our support team if you need more help.
WrongDatacenter
The API key provided is linked to a different data center.
This error suggests that you tried to contact the wrong data center. It's often associated with misconfigured libraries.

### 404

ResourceNotFound
The requested resource could not be found.
This error tells you a specific resource doesn't exist. It's possible that the resource has been moved or deleted, or that there's a typo in your request.

### 405

MethodNotAllowed
The requested method and resource are not compatible. See the Allow header for this resource's available methods.
This error means that the requested resource does not support the HTTP method you used. Find out which methods are allowed for each resource in the API Reference.

### 414

ResourceNestingTooDeep
The sub-resource requested is nested too deeply.
This uncommon error appears if you've tried to generate a URL with too many resources.

### 422

InvalidMethodOverride
You can only use the X-HTTP-Method-Override header with the POST method.
This error lets you know you've tried to override an incompatible method. The Mailchimp API only permits method override with POST.
RequestedFieldsInvalid
The fields requested from this resource are invalid.
This error suggests there is a typo in your field request or some other type of syntax error or problem that invalidates your request.

### 429

TooManyRequests
You have exceeded the limit of 10 simultaneous connections.
When you reach the connection limit, we'll throttle server response. If any of your requests time out after you've reached the limit, those requests could still be considered open and continue to slow your connection. Contact the Exchange support team at exchange.support@se.com if you think this is the case.

### 500

InternalServerError
An unexpected internal error has occurred. Please contact Support for more information.
This error lets you know our servers have experienced a problem. Although this is rare, please contact exchange.support@se.com to let us know that you've encountered this error.

### 503

ComplianceRelated
This method has been disabled.

# Support

Contact the Exchange support team at exchange.support@se.com.

In your request please :

	- mention the involved endpoint
	- give the request that generate the error
	- copy past any error message you received
	- add some screen shot

# Blogs

---

# API Reference
