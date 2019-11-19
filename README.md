# _Calendly_ Open Microservice

> Leverage Calendly’s API

[![Open Microservice Specification Version](https://img.shields.io/badge/Open%20Microservice-1.0-477bf3.svg)](https://openmicroservices.org) [![Open Microservices Spectrum Chat](https://withspectrum.github.io/badge/badge.svg)](https://spectrum.chat/open-microservices) [![Open Microservices Code of Conduct](https://img.shields.io/badge/Contributor%20Covenant-v1.4%20adopted-ff69b4.svg)](https://github.com/oms-services/.github/blob/master/CODE_OF_CONDUCT.md) [![Open Microservices Commitzen](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

## Introduction

This project is an example implementation of the [Open Microservice Specification](https://openmicroservices.org), a standard originally created at [Storyscript](https://storyscript.io) for building highly-portable "microservices" that expose the events, actions, and APIs inside containerized software.

## Getting Started

The `oms` command-line interface allows you to interact with Open Microservices. If you're interested in creating an Open Microservice the CLI also helps validate, test, and debug your `oms.yml` implementation!

See the [oms-cli](https://github.com/microservices/oms) project to learn more!

### Installation

```
npm install -g @microservices/oms
```

## Usage

### Open Microservices CLI Usage

Once you have the [oms-cli](https://github.com/microservices/oms) installed, you can run any of the following commands from within this project's root directory:

#### Actions

##### create

> Create a webhook subscription. Receive Calendly appointment data in real-time at a specified URL when a Calendly event is scheduled or cancelled.
##### Action Arguments

| Argument Name | Type | Required | Default | Description |
|:------------- |:---- |:-------- |:--------|:----------- |
| url | `string` | `false` | None | Where should we send webhooks to? Ex: https://mywebsite.com/webhooks/invitee_created |
| events | `string` | `false` | None | Array of event names, options: invitee.created or invitee.canceled |
| API_KEY | `string` | `true` | None | Get from https://developer.calendly.com/docs/getting-your-authentication-token  |

``` shell
oms run create \ 
    -a url='*****' \ 
    -a events='*****' \ 
    -e API_KEY=$API_KEY
```

##### subscribe

> Any of your Webhook Subscriptions can be accessed by ID using this endpoint.
##### Action Arguments

| Argument Name | Type | Required | Default | Description |
|:------------- |:---- |:-------- |:--------|:----------- |
| hooksId | `string` | `false` | None | Calendly ID of the Webhook to subscribe to. |
| API_KEY | `string` | `true` | None | Get from https://developer.calendly.com/docs/getting-your-authentication-token  |

``` shell
oms run subscribe \ 
    -a hooksId='*****' \ 
    -e API_KEY=$API_KEY
```

##### subscribeList

> You can view your current Webhook Subscriptions. Using this endpoint will list up to the first 100 Webhook Subscriptions, and it will order active subscriptions first. If this endpoint does not list the Webhook Subscription that you need information for, you can find it by ID, or delete the ones you don't need anymore.
##### Action Arguments

| Argument Name | Type | Required | Default | Description |
|:------------- |:---- |:-------- |:--------|:----------- |
| API_KEY | `string` | `true` | None | Get from https://developer.calendly.com/docs/getting-your-authentication-token  |

``` shell
oms run subscribeList \ 
    -e API_KEY=$API_KEY
```

##### delete

> Any of your Webhook Subscriptions can be deleted by ID using this endpoint.
##### Action Arguments

| Argument Name | Type | Required | Default | Description |
|:------------- |:---- |:-------- |:--------|:----------- |
| hooksId | `string` | `false` | None | Calendly ID for the Webhook. |
| API_KEY | `string` | `true` | None | Get from https://developer.calendly.com/docs/getting-your-authentication-token  |

``` shell
oms run delete \ 
    -a hooksId='*****' \ 
    -e API_KEY=$API_KEY
```

##### eventType

> Event Types contain the most important configurations in Calendly. If you need some basic information about your event types, you can use this endpoint.
##### Action Arguments

| Argument Name | Type | Required | Default | Description |
|:------------- |:---- |:-------- |:--------|:----------- |
| API_KEY | `string` | `true` | None | Get from https://developer.calendly.com/docs/getting-your-authentication-token  |

``` shell
oms run eventType \ 
    -e API_KEY=$API_KEY
```

##### about

> Use this endpoint to request basic information about yourself. This might be helpful if you're building functionality for multiple Calendly users.
##### Action Arguments

| Argument Name | Type | Required | Default | Description |
|:------------- |:---- |:-------- |:--------|:----------- |
| API_KEY | `string` | `true` | None | Get from https://developer.calendly.com/docs/getting-your-authentication-token  |

``` shell
oms run about \ 
    -e API_KEY=$API_KEY
```

## Contributing

All suggestions in how to improve the specification and this guide are very welcome. Feel free share your thoughts in the Issue tracker, or even better, fork the repository to implement your own ideas and submit a pull request.

[![Edit calendly on CodeSandbox](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/github/oms-services/calendly)

This project is guided by [Contributor Covenant](https://github.com/oms-services/.github/blob/master/CODE_OF_CONDUCT.md). Please read out full [Contribution Guidelines](https://github.com/oms-services/.github/blob/master/CONTRIBUTING.md).

## Additional Resources

* [Install the CLI](https://github.com/microservices/oms) - The OMS CLI helps developers create, test, validate, and build microservices.
* [Example OMS Services](https://github.com/oms-services) - Examples of OMS-compliant services written in a variety of languages.
* [Example Language Implementations](https://github.com/microservices) - Find tooling & language implementations in Node, Python, Scala, Java, Clojure.
* [Storyscript Hub](https://hub.storyscript.io) - A public registry of OMS services.
* [Community Chat](https://spectrum.chat/open-microservices) - Have ideas? Questions? Join us on Spectrum.
