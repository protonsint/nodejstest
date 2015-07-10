Node.js test app
----------------
To test an S2I build.

To create app in openshift console.

1. Select the project, such as "demo".
2. Click the "Create" button.
3. Enter the location of the source in Git, e.g. http://hawaii.local/test.git
4. Click "Next".
5. Adjust the name if needed.
6. Uncheck "create a route to the application" - we will create route as a secondary step. OPTIONAL if you have your subdomain setup correctly you can let it create the route
7. Click  "Create" - wait for the first build to start (on its own) and complete- if it fails use "oc build-logs [build-name] -n [project-name]"
8. Create a JSON file to define the route changing the relevant fields to match th service name, a unique name for the route, FQDN such as test.cloudapps.example.com (depends on your BIND setup) - SKIP THIS STEP and STEP 9 if you let OSE create the route in step 6
9. Create the route "oc create -f [JSON file name] -n [project-name]"
10. You should be able to access the application at http://[FQDN] - This app listens on port 80
