# [JAVASERVERFACES_SPEC_PUBLIC-1423](https://java.net/jira/browse/JAVASERVERFACES_SPEC_PUBLIC-1423) Reproducer

This project is a reproducer for [JAVASERVERFACES_SPEC_PUBLIC-1423](https://java.net/jira/browse/JAVASERVERFACES_SPEC_PUBLIC-1423): Dynamic resource loading in ajax requests

## Steps to reproduce:

1. Clone the project:

        git clone https://github.com/stiemannkj1/dynamic-resource-loading-ajax-reproducer.git

2. Build the project with maven. You can use the `myfaces` profile to use myfaces instead of mojarra (for example: `-P myfaces`). You can use the `jsf.version` property to change the version of JSF being used (for example: `-Djsf.verison=2.3.0-m06`).

        cd dynamic-resource-loading-ajax-reproducer && mvn clean install

3. Deploy the project to tomcat:

        cp target/dynamic-resource-loading-ajax-reproducer*.war $TOMCAT_HOME/webapps/

### Steps to reproduce by programmatically (dynamically) adding a component with a `@ResourceDepedency` to the view via java:

1. Verify that the **`example.js`** resource dependency is loaded when the `<example:component rendered="false" />` is included in the facelet view:

    1. Navigate to **`static.faces`** in the browser:

        [http://localhost:8080/dynamic-resource-loading-ajax-reproducer-1.0-SNAPSHOT/static.faces](http://localhost:8080/dynamic-resource-loading-ajax-reproducer-1.0-SNAPSHOT/static.faces)

    2. Verify that an alert with the text "example.js resource loaded" appears.

2. Navigate to **`dynamic.faces`** in the browser:

      [http://localhost:8080/dynamic-resource-loading-ajax-reproducer-1.0-SNAPSHOT/dynamic.faces](http://localhost:8080/dynamic-resource-loading-ajax-reproducer-1.0-SNAPSHOT/dynamic.faces)

3. Click the *Add Example Component Via Ajax* button.

If the feature does not exist, "**example:component rendered**" will appear, but the alert showing that **`example.js`** was loaded will not appear.

If the feature exists then an alert with the text "example.js resource loaded" will appear.

### Steps to reproduce by programmatically (dynamically) changing the `src` attribute of a `ui:include` tag:

1. Verify that the **`example.js`** resource dependency is loaded when the `<example:component />` is included statically:

    1. Navigate to **`staticInclude.faces`** in the browser:

        [http://localhost:8080/dynamic-resource-loading-ajax-reproducer-1.0-SNAPSHOT/staticInclude.faces](http://localhost:8080/dynamic-resource-loading-ajax-reproducer-1.0-SNAPSHOT/staticInclude.faces)

    2. Verify that an alert with the text "example.js resource loaded" appears.

2. Navigate to **`dynamicInclude.faces`** in the browser:

      [http://localhost:8080/dynamic-resource-loading-ajax-reproducer-1.0-SNAPSHOT/dynamicInclude.faces](http://localhost:8080/dynamic-resource-loading-ajax-reproducer-1.0-SNAPSHOT/dynamicInclude.faces)

3. Click the *Toggle Include* button.

If the feature does not exist, "**example:component rendered**" will appear, but the alert showing that **`example.js`** was loaded will not appear.

If the feature exists then an alert with the text "example.js resource loaded" will appear.
