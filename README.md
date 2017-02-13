Watson IoT Platform Starter for Bluemix with Node-RED Application
=================================================================

### Node-RED in BlueMix

This repository is an example Node-RED application that can be deployed into
Bluemix with only a couple clicks. Try it out for yourself right now:


If you have a Trial, Premium or Paygo Bluemix account, click one of these buttons:

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=) (via JazzHub)

[![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://console.ng.bluemix.net/devops/setup/deploy?repository=) (via Continuous Delivery)

If you have a Standard Bluemix account

### Deploying from local command-line

Install all the required CLI tools: [Bluemix CLI](http://clis.ng.bluemix.net/), [cf CLI](https://docs.cloudfoundry.org/cf-cli/install-go-cli.html), [git](https://git-scm.com/downloads), etc. More details in Bluemix docs [CLI and Dev Tools](bluemix.net/docs/cli/index.html).

Create the required services:

`cf create-service iotf-service iotf-service-free iotp-starter`

`cf create-service cloudantNoSQLDB Lite iotp-starter-cloudantNoSQLDB`

Clone this repository locally:

`git clone <this URL> [](./)` [](./)

Push the app to Bluemix:

`cf push <your app name>`

### How does this work?

When you click the button, you are taken to Bluemix where you get a pick a name
for your application at which point the platform takes over, grabs the code from
this repository and gets it deployed.

It will automatically create an instance of the IBM Watson Internet of Things (IoT) Platform service, call it
`iotp-starter` and bind it to you app. This is where all your IoT devices send their sensor data, and where Node-RED and other application get the IoT data sent from. If you deploy multiple instances of
Node-RED from this repository, they will share the one Watson IoT Platform instance.

It will automatically create an instance of the Cloudant service, call it
`iotp-starter-cloudantNoSQLDB` and bind it to you app. This is where your
Node-RED instance will store its data. If you deploy multiple instances of
Node-RED from this repository, they will share the one Cloudant instance.

It includes a set of default flows that are automatically deployed the first time
Node-RED runs.


### Customising Node-RED

This repository is here to be cloned, modified and re-used to allow anyone create
their own Node-RED based application that can be quickly deployed to Bluemix.

The default flows are stored in the `defaults` directory in the file called `flow.json`.
When the application is first started, this flow is copied to the attached Cloudant
instance. When a change is deployed from the editor, the version in cloudant will
be updated - not this file.

The web content you get when you go to the application's URL is stored under the
`public` directory.

Additional nodes can be added to the `package.json` file and all other Node-RED
configuration settings can be set in `bluemix-settings.js`.

If you do clone this repository, make sure you update this `README.md` file to point
the `Deploy to Bluemix` button at your repository.

If you want to change the name of the Cloudant instance that gets created, the memory
allocated to the application or other deploy-time options, have a look in `manifest.yml`.
