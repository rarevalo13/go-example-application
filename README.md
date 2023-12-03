# Go SSO & Directory Sync Example

An example Go Application demonstrating how to use the WorkOS Go SDK to authenticate users via SSO using Okta as an IdP and Directory Sync. 

---

### Prerequisites

- Go
    
    You can ensure you have Go installed by running `go version` in your terminal, if you do not have go installed, you can installed it via homebrew by running `brew install go` or by downloading and installing the binary from [here](https://go.dev/doc/install).
    
- An Okta Account
    
    You can sign up for a developer account with Okta [here](https://developer.okta.com/signup/).
    
- A WorkOS Account
    
    If you do not already have a WorkOS account, you can sign up [here](https://dashboard.workos.com/signup).
    

---

### Go Project Setup

1. Clone this git repository using your preferred secure method (HTTPS or SSH)
    
    ```
    #HTTPS
    git clone https://github.com/rarevalo13/go-example-application.git
    ```
    

 or
   ```
   #SSH
   git clone git@github.com:rarevalo13/go-example-application.gitq
   ```

1. Once you have cloned the repository navigate to the root directory 
    
    ```
    cd go-example-application 
    ```
    
2. Obtain and make notes of the following values in your WorkOS account. 
    - WorkOS API Key
    - WorkOS Client ID
    - Redirect URI <this should be set to https://localhost:8000/callback,  as well as in your WorkOS Redirects sections which can be found under the Developer heading in your dashboard on the left hand side.
    - WorkOS Connection ID
    - WorkOS Directory ID

1. Once you’ve taken note of that, you create a `.env` file and fill in the values from step 3. 

---

### Okta SSO Setup with WorkOS

Once you’ve set up your developer account with Okta you’ll need to log in and create two applications under the Applications menu in your developer admin. You’ll want to create a SAML 2.0 application for the SSO integration, we have a guide on how to create it specifically for Okta  [here](https://workos.com/docs/integrations/okta-saml).

If you don’t have any users currently in Okta, you’ll want to create a few, you can do so by following the guide from Okta on how to create new users [here](https://help.okta.com/en-us/content/topics/users-groups-profiles/usgp-add-users.htm). 

The second application will be the directory sync Application which you can browser the application catalog by searching “bearer token” and you should see an application called SCIM 2.0 Test App (OAuth Bearer Token).  Once you’ve created that app, you can can follow along with our Okta specific guide that can be found [here](https://workos.com/docs/integrations/okta-scim). 

---

### Running the local server

Once you have set up the two applications and configured them per the guides, you can navigate to your terminal and run the local server by running `go run main.go` this will start a local server on port 8000. If you navigate to [localhost:8000](http://localhost:8000) you should see a sign on display with 3 options. clicking on the Okta option should bring you to the Okta login screen and you’d log in using any user that was created and assigned the application you created with this tutorial.