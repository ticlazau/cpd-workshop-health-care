# Watson Knowledge Catalog for Admins

This exercise demonstrates how to solve the problems of enterprise data governance using Watson Knowledge Catalog on the Cloud Pak for Data platform. We'll explain how to use governance, data quality and active policy management in order to help your organization protect and govern sensitive data, trace data lineage and manage data lakes. This knowledge will help users quickly discover, curate, categorize and share data assets, data sets, analytical models and their relationships with other members of your organization. It serves as a single source of truth for data engineers, data stewards, data scientists and business analysts to gain self-service access to data they can trust.

You will need the *Admin* role to create a catalog.

This section is comprised of the following steps:

1. [Set up Catalog](#1-set-up-catalog)
1. [Add Data Assets](#2-add-data-assets)
1. [Add collaborators and control access](#3-add-collaborators-and-review-data)
1. [Add categories](#4-add-categories)
1. [Add data classes](#5-add-data-classes)
1. [Add Business terms](#6-add-business-terms)
1. [Add rules for policies](#7-add-rules-for-policies)

## 1. Set up Catalog

> NOTE: The default catalog is your enterprise catalog. It is created automatically after you install the Watson Knowledge Catalog service and is the only catalog to which advanced data curation tools apply. The default catalog is governed so that data protection rules are enforced. The information assets view shows additional properties of the assets in the default catalog to aid curation. Any subsequent catalogs that you create can be governed or ungoverned, do not have an information assets view, and supply basic data curation tools.

First we'll create a catalog and load some data

### Create the catalog

* Go to the upper-left (☰) hamburger menu and choose `Organize` -> `All catalogs`.

  ![open catalog menu](../images/wkc-admin/wkc-admin-open-catalog-menu.png)

* From the *Your catalogs* page, click the `Create catalog` button.

  ![create WKC catalog](../images/wkc-admin/wkc-create-catalog.png)

* Give your catalog a name, check the `Enforce data protection rules` checkbox and provide an optional description. Then click the `Create` button.

  ![name and create wkc catalog](../images/wkc-admin/wkc-admin-name-create-catalog.png)

> *Note: Click `Ok` in the pop up window when selecting the data protection checkbox.*

## 2. Add Data Assets

There are several ways to add assets to the catalog. We are going to add a local data asset. There are also optional sections to add connection assets below.

### Local Data Asset

* Click `Add to Catalog +` in the top right and choose `Local files`.

  ![add local files to catalog](../images/wkc-admin/wkc-admin-add-local-files.png)

* Click the `browse` link in the 'Select file(s) panel. Browse to the where you cloned the git repository for this workshop or where you downloaded the data assets and choose `data/patients.csv` file to select it. Add an optional description and click the `Add` button.

  ![click add for local files to catalog](../images/wkc-admin/wkc-admin-file-selected-now-add.png)

  > *NOTE: Stay in the catalog until loading is complete! If you leave the catalog, the incomplete asset will be deleted.*

* The newly added file will show up under the *Browse Assets* tab of your catalog:

  ![newly added data in catalog](../images/wkc-admin/wkc-admin-browse-assets.png)

### (Optional) Add Connection

> Note: This is an optional part of the lab. You will only be able to add a remote database connection if you have the proper admin credential. You should skip this, unless instructed to add a database connection by the lab instructors.

* You can add a connection to various data sources, for example *DB2 Warehouse in IBM Cloud*, by choosing `Add to Catalog +` -> `Connection`:

  ![add connection to catalog](../images/wkc-admin/wkc-add-connection.png)

* Click on the data source type you want to add (for example, `Db2 Warehouse`).

  ![chose db2 warehouse connection ](../images/wkc-admin/wkc-choose-db2-warehouse-conn.png)

* Enter the connection details and click `Create`:

  ![enter db2 warehouse connection details](../images/wkc-admin/wkc-enter-connection-details.png)

* The connection now shows up in the catalog.

**Note: Virtualized data can be added to the *Default* catalog by someone with Administrator or Editor access to that catalog. There is an option to add `Data Virtualization` as a connection.**

### (Optional) Add Data from Connection

> Note: This is an optional part of the lab. You should skip this, unless instructed to add virtualized data by the lab instructors.

Once you have a connection to a data source, you will be able to add assets from that connection.

* Click `+Add to Catalog` -> `Connected asset`:

  ![add connected asset](../images/wkc-admin/wkc-add-connected-asset.png)

* Click *Source* -> `Select source`. Browse under `DV` to you Schema (i.e. UserXYZW) and choose the joined table. Click `Select`.

A user can now add this to a project like any other asset from a catalog.

## 2. Add Collaborators and Review Data

* Under the *Access Control* tab you can click `Add Collaborator` to give other users access to your catalog.

  ![give users access to the catalog](../images/wkc-admin/wkc-admin-access-control-add-collaborator.png)

* You can search for a user by entering their name in the `Collaborators` field. Click on the name to select the user.

  ![Search for collaborator](../images/wkc-admin/wkc-admin-add-user.png)

* You can choose a role for the user - `Admin`, `Editor`, or `Viewer`. Then click the `Add` button.

  ![choose role for collaborator](../images/wkc-admin/wkc-admin-user-role-choice.png)

* To access data in the catalog, click on the name of the data.

  ![click data name to open](../images/wkc-admin/wkc-admin-click-data-name-to-open.png)

* A preview of the data will open, with metadata and the first few rows.

  ![preview of data](../images/wkc-admin/wkc-admin-data-preview.png)

* You can click the `Review` tab and rate the data, as well as comment on it, to provide feedback to consumers of the data.

  ![review data](../images/wkc-admin/wkc-admin-review-data.png)

## 3. Add categories

The fundamental abstraction in Watson Knowledge Catalog is the Category. A category is analogous to a folder. You can add categories as needed, or you can import them in .csv format.

### Import categories

> Note: There are no import files for categories supplied for this lab. This section is just for information only.

* Import a category for your assets by going to the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Categories`, then the click `Import` button.

  ![Import categories](../images/wkc-admin/wkc-import-categories.png)

* Click the `Add file` and navigate to where you cloned/downloaded the workshop repository, choosing `data/wkc/glossary-organize-categories.csv`. Click the `Next` button.

  ![Import select file](../images/wkc-admin/wkc-import-select-file.png)

* Under `Select merge option` choose `Replace all values` and click `Import`.

  ![Import select merge option](../images/wkc-admin/wkc-import-select-merge-option.png)

* You will see "The import completed succesfully" when it is completed.

* In this way, you can import Categories, Business Terms, Classifications, Policies, etc. to populate your governance catalogs.

### Add category manually

* In addition to importing, you can manually create categories. Add a category for your assets by going to the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Categories`, then click the `Create category` button on the top right.

  ![organize data categories](../images/wkc-admin/wkc-menu-organize-categories.png)

* Give your category a name, such as *Personal Data*, and an optional description, and then click the `Save` button.

  ![new category billing](../images/wkc-admin/wkc-admin-new-category-personal-data.png)

* Now, if you hit the `Create category` link on the *Personal Data* category screen, you can create a subcategory, such as *Residence Information*.

  ![sub category residence information](../images/wkc-admin/wkc-admin-new-subcategory-residence-information.png)

* For the *Personal Data* category you can select a *Type*, such as `Business term`.

  ![select business term type](../images/wkc-admin/wkc-admin-category-select-type.png)

* We can also create classifications for assets, similar to *Confidential*, *Personally Identifiable Information*, or *Sensitive Personal Information* in a similar way, by going to the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Classifications`.

  ![select classification](../images/wkc-admin/wkc-navigate-classifications.png)

* Click on the `New classification` button on the top right and then `Create new classification` from the drop down menu. These classifications can then be added to your category as a *Type*:

  ![select classification type](../images/wkc-admin/wkc-add-classifications.png)

## 4. Add data classes

When you profile your assets, a data class will be inferred from the contents where possible. We'll see more on this later. You can also add your own data classes.

* Add a data class for your assets by going to the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Data class`, then click the `New data class` button and subsequent `Create new data class` option from the drop down menu.

  ![organize data classes](../images/wkc-admin/wkc-menu-organize-data-classes.png)

* Give your new data class a name, i.e. *alphanumeric*, and an optional Primary category and/or description, and click `Save as draft`.

  ![new data class](../images/wkc-admin/wkc-create-data-class.png)

* Once the data class is created, we can optionally: add *Stewards* for this class, and associate *classifications* and *business terms*. When you are ready, click the `Publish` button and again `Publish` in the pop up window.

  ![tools for data class](../images/wkc-admin/wkc-data-class-add-term-publish.png)

* Now let's add that data class to a column in our *patients.csv* asset.

* Go back to the catalog you created earlier (i.e *HealthCareCatalog*) and open it ((☰) hamburger menu `Organize` -> `All catalogs` and choose `HealthCareCatalog`). Under the *Browse assets* tab, click on the data set *patients.csv* to get the column/row preview. Find the *ID* column and click the down arrow next to "Text" and then *View all*:

  ![change data class](../images/wkc-admin/wkc-admin-existing-data-class.png)

* In the window that opens, search for your newly created data class, *alphanumeric* and click it when it returns in the search. Then click the `Select` button.

  ![Set colunn to numerical data class](../images/wkc-admin/wkc-admin-numeric-data-class.png)

## 5. Add Business terms

You can use [Business terms](https://dataplatform.cloud.ibm.com/docs/content/wsj/governance/dmg16.html) to standardize definitions of business concepts so that your data is described in a uniform and easily understood way across your enterprise.

You already saw how to create a category and make it a *business term*. You can also create the business term as it's own entity.

* From the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Business terms`:

  ![organize Data Business terms](../images/wkc-admin/wkc-admin-organize-data-business-terms.png)

* Click on the upper-right `New business term` button and then the `Create new business term` option in the drop down menu.

  ![create business term](../images/wkc-admin/wkc-create-business-term.png)

* Give the new Business term a name such as *Contact Information* and optional description (**NOTE: If you are working with others on the same platform, prepend your term with something unique, i.e scottda-ContactInfo**). Click the `Save as draft` button.

  ![name new business term](../images/wkc-admin/wkc-admin-name-business-term.png)

* A window will come up once the term is created. You can see a rich set of options for creating related terms and adding other metadata. For now, click `Publish` to make this term available to users of the platform. Go ahead and click `Publish` on the pop up confirmation window.

  ![publish business term](../images/wkc-admin/wkc-admin-publish-business-term.png)

* Go back to the catalog you created earlier (i.e *HealthCareCatalog*) and open it ((☰) hamburger menu `Organize` -> `All catalogs` and choose `HealthCareCatalog`). Under the *Browse assets* tab, click on the data set *patients.csv* to get the column/row preview. Find the *ADDRESS* column and click the *Column information* icon (looks like an "eye").

  ![choose ADDRESS columnn information](../images/wkc-admin/wkc-admin-address-column-information.png)

* In the window that opens, click the *edit* icon (looks like a "pencil") next to *Business terms* :

  ![edit business terms](../images/wkc-admin/wkc-admin-assign-terms-to-column.png)

* Enter *Contact Information* (or your uniquely named term such as *scottda-ContactInfo*) term you created earlier under *Business terms* and the term will be searched for. Click on the `Contact Information` term that is found, and click `Apply`:

  ![search business terms](../images/wkc-admin/wkc-admin-search-contact-to-assign-term.png)

* Close that window once the term has been applied. Now, if you wish, do the same thing to add the *Contact Information* Business term to the *CITY*, *STATE*, and *ZIP* columns.

* You will now be able to search for these terms from within the platform. For example, going back to your top level *HealthCareCatalog*, in the search bar with the comment "What assets are you searching for?" enter your unique *<unique_string>Contact Information* term:

  ![search using business terms](../images/wkc-admin/wkc-admin-search-business-terms.png)

* The *patients.csv* data set will show up, since it contains columns tagged with the *Contact Infomation* business term.

## 6. Add rules for policies

We can now create rules to control how a user can access data.

* Create a business term called *PatientID* and assign it to your *ID* column in the data set `patients.csv` file using the instructions above. See below if you need details, but try it yourself first, and skip to *Adding a rule* below if you do not need a reminder.

### How to create a Business term review

* From the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Business terms`.

* Click on the upper-right `+ Create Business term` button.

* Give the new Business term the name *PatientID* and optional description, and click `Save as draft`. In the next window, click `Publish`.

* Now go back to your *HealthCareCatalog* by opening it up to the column view ((☰) hamburger menu `Organize` -> `All catalogs` and choose `HealthCareCatalog`). Under the *Browse assets* tab, click on the data set *patients.csv* to get the column/row preview. Find the *ID* column and click the *Column information* icon (looks like an "eye").

* In the window that opens, click the *edit* icon (looks like a "pencil") next to *Business terms* .

* Enter *PatientID* under *Business terms* and the term will be searched for. Click on the `CustumerID` term that is found, and click `Apply`. Then close the pop up window.

### Adding a rule

* From the upper-left (☰) hamburger menu, choose `Organize` -> `Data and AI Governance` -> `Rules`.

* Click the `New rule` button on the top right and then select the  `Create new rule` option from the drop down menu.

* In the 'Create a new rule' page, select the `Data protection rule` option.

  ![Data protection rule](../images/wkc-admin/wkc-new-dataprotection-rule.png)

* Give your rule a *Name*, leave the *Type* set to `Access`, and add a *Business definition*.

* Under *Rule builder* > *Condition1*: For the `If` condition, select *Business term* *Contains any* *PatientID*. Under *Action*, for the `then` panel, select *mask data* *in columns containing* *alphanumeric*. Choose the tile for `Substitute`, which will make a non-identifiable hash. This obscures the actual ID, but allows actions like database joins to still work. Click the `Create rule` button.

  ![define rule for masking customerID](../images/wkc-admin/wkc-rule-substitute-customer-id.png)

* Now if we go back to our *patients.csv* asset in the catalog at the *ID* column, it will look the same as before. But a non-admin user will see the "lock" icon and see that the customerID has now been substituted with a hash value.

* To add a rule to *Obfuscate* data, follow the prior instructions and build a new data protection rule to *Obfuscate* the *Gender*

  ![Gender obfuscate rule ](../images/wkc-admin/wkc-admin-create-obfuscate-rule.png)

* And now when that column is viewed by a non-admin user, it will have data that is replaced with similarly formatted data.

## Conclusion

In this lab, we learned how to:

* Set up Catalog and Data
* Add collaborators and control access
* Add categories
* Add data classes
* Add Business terms
* Add rules for policies
