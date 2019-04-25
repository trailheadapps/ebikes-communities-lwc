# E-Bikes Communities Lightning Web Components Sample Application

[![CircleCI](https://circleci.com/gh/trailheadapps/ebikes-communities-lwc.svg?style=svg)](https://circleci.com/gh/trailheadapps/ebikes-communities-lwc)

![ebikes-logo](ebikes-logo.png)

E-Bikes is a sample application that demonstrates how to build applications with Lightning Web Components. E-Bikes is a fictitious electric bicycle manufacturer. The application helps E-Bikes manage their products and reseller orders using a rich user experience.

> Currently a known issue exists with Communities in combination with [PageReferences](https://developer.salesforce.com/docs/component-library/documentation/lwc/lwc.reference_page_reference_type). Occasionally the navigating to a product record page in the expand icon on the product card in the product explorer page doesn't navigate/work. For a workaround, when this happens, if you refresh the page and then click again, it will navigate. This will be fixed in Summer '19.

## Table of contents

-   Installation Instructions

    -   [Installing E-Bikes using a scratch org](#installing-e-bikes-using-a-scratch-org)

-   [Optional installation instructions](#optional-installation-instructions)
-   [Application Walkthrough](#application-walkthrough)

## Installing E-Bikes using a Scratch Org

1. Set up your environment. Follow the steps in the [Quick Start: Lightning Web Components](https://trailhead.salesforce.com/content/learn/projects/quick-start-lightning-web-components/) Trailhead project. The steps include:

-   Enable Dev Hub in your Trailhead Playground
-   Install Salesforce CLI
-   Install Visual Studio Code
-   Install the Visual Studio Code Salesforce extensions, including the Lightning Web Components extension

2. If you haven't already done so, authenticate with your hub org and provide it with an alias (**myhuborg** in the command below):

```
sfdx force:auth:web:login -d -a myhuborg
```

3. Clone the repository:

```
git clone https://github.com/trailheadapps/ebikes-communities-lwc.git
cd ebikes-communities-lwc
```

4. Create a scratch org and provide it with an alias (**ebikes** in the command below):

```
sfdx force:org:create -s -f config/project-scratch-def.json -a ebikes
```

5. Push the app to your scratch org:

```
sfdx force:source:push
```

6. Assign the **ebikes** permission set to the default user:

```
sfdx force:user:permset:assign -n ebikes
```

7. Load sample data:

```
sfdx force:data:tree:import --plan ./data/sample-data-plan.json
```

8. Deploy Community metadata

```
sfdx force:mdapi:deploy -u ebikes --deploydir mdapiDeploy/unpackaged -w 1
```

9. Open the scratch org:

```
sfdx force:org:open
```

10. In **Setup**, under **Themes and Branding**, activate the **Lightning Lite** theme.

11. In **Setup**, select **All Communities**. Click on **Builder** for the _E-Bikes_ Community.

12. Click **Publish**, to publish the community. Click on the workspace icon in the top left corner, then click **View E-Bikes** to see the live community.

## Optional Installation Instructions

This repository contains several files that are relevant if you want to integrate modern web development tooling to your Salesforce development processes, or to your continuous integration/continuous deployment processes.

### Code formatting

[Prettier](https://prettier.io/) is a code formatter used to ensure consistent formatting across your code base. To use Prettier with Visual Studio Code, install [this extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) from the Visual Studio Code Marketplace. The [.prettierignore](/.prettierignore) and [.prettierrc](/.prettierrc) files are provided as part of this repository to control the behavior of the Prettier formatter.

### Code linting

[ESLint](https://eslint.org/) is a popular JavaScript linting tool used to identify stylistic errors and erroneous constructs. To use ESLint with Visual Studio Code, install [this extension](https://marketplace.visualstudio.com/items?itemName=salesforce.salesforcedx-vscode-lwc) from the Visual Studio Code Marketplace. The [.eslintignore](/.eslintignore) file is provided as part of this repository to exclude specific files from the linting process in the context of Lighning Web Components development.

### Pre-commit hook

This repository also comes with a [package.json](./package.json) file that makes it easy to set up a pre-commit hook that enforces code formatting and linting by running Prettier and ESLint every time you `git commit` changes.

To set up the formatting and linting pre-commit hook:

1. Install [Node.js](https://nodejs.org) if you haven't already done so
2. Run `npm install` in your project's root folder to install the ESLint and Prettier modules (Note: Mac users should verify that Xcode command line tools are installed before running this command.)

> Note: This projects also contains [Jest](https://jestjs.io) tests for unit testing Lightning Web Components. If you experience errors regarding `deasync` when running `npm install` please check out the troubleshooting information in the [lwc-jest repository](https://github.com/salesforce/lwc-jest#troubleshooting-deasync-installation-errors).

Prettier and ESLint will now run automatically every time you commit changes. The commit will fail if linting errors are detected. You can also run the formatting and linting from the command line using the following commands (check out [package.json](./package.json) for the full list):

```
npm run lint:lwc
npm run prettier
```

## Salesforce Application Walkthrough

### Product Explorer

1. Click the **Product Explorer** tab.

2. Filter the list using the filter component in the left sidebar.

3. Click a product in the tile list to see the details in the product card.

4. Click the expand icon in the product card to navigate to the product record page.

### Product Record Page

1. The product record page features a **Similar Products** component.

2. Click the **View Details** button to navigate to a similar product record page.

### Reseller Orders

1. Click the down arrow on the **Reseller Order** tab and click **New Reseller Order**.

2. Select an account, for example **Wheelworks** and click **Save**.

3. Drag a product from the product list on the right onto the gray panel in the center. The product is automatically added to the order as an order item.

4. Modify the ordered quantity for small (S), medium (M), and large (L) frames and click the save button (checkmark icon).

5. Repeat steps 3 and 4 to add more products to the order.

6. Mouse over an order item tile and click the trash can icon to delete an order item from the order.

### Account Record Page

The account record page features an **Account Map** component that locates the account on a map.

## Communities Application Walkthrough

### Home

1. See the custom hero component in Communities that pulls in rich assets and navigates to the product or product family that is configured.

2. Check all the properties exposed in the hero component in Community Builder.

### Create Case

1. Select the _My Cases_ list view in the record list on the right side of the page.

2. Fill in the details of the case on the left side of the page.

3. Click on Create Case and see the record list to be updated with your new case.

### Product Explorer

1. Click the **Product Explorer** tab.

2. Filter the list using the filter component in the left sidebar.

3. Click a product in the tile list to see the details in the product card.

4. Click the expand icon in the product card to navigate to the product record page.

### Product Record Page

1. The product record page features a **Similar Products** component.

2. Click the **View Details** button to navigate to a similar product record page.
