# Trello-API-Hook
API Hook that provides the automation of the Authentication and Authorisation for calls to the Trello API
## Trello API 
### About the API
- Access, edit, create, and save Boards, Lists, Cards, etc, to/from your Trello account.
- API Documentation: [Trello API docs] (https://trello.com/docs/index.html)

### Pre-Reqs
- while logged into your Trello Account:
    - generate an application key by typing this into your browser: https://trello.com/1/appKey/generate
    - Save the Key and secret from the result
    - Then, generate a non-expiring read/write token by typing this into your browser: https://trello.com/1/authorize?key=substitutewithyourapplicationkey&name=My+Application&expiration=never&response_type=token&scope=read,write
    - save the non-expiry token

### Getting Started Instructions
#### Download and Import
- Download TrelloAPIHook.zip
- Login to PolicyManager  example: http://localhost:9900
- Select the root "Registry" organisation and click on the "Import Package" from the Actions navigation window on the right side of the screen
  - click on button to browse for the TrelloAPIHook.zip archive file 
  - make sure select the migrations.properties file 
  - click Okay to start the importation of the hook.
- this will create a "Trello API Hook" Organisation with the requisite artefacts needed to run the API.

#### Verify Import
- Expand the services folder in the Trello API Hook organisation you imported and find Trello_vs0 VS

#### Activate Anonymous Contract
- Expand the contracts folder in the Trello API Hook organisation you imported and find the "Anonymous" contract under the "Provided Contracts" folder
- click on the "Activate Contract" workflow activity in the righ-hand Activities portlet
- ensure that the status changes to "Workflow Is Completed"

#### Configure Security
- Go to Trello Hook -> Policies -> Operational Policies 
    - For the four Policies defined there:
        - select a policy
        - click on the "Activate Policy" workflow activity in the righ-hand Activities portlet
        - ensure that the status changes to "State: Active"
    - Go to the PM "Security" tab
    - Click the "Add User" button
    - make the "Username" the value of the Key you generated as part of the pre-requisites
    - make the "password" the value of the Token you generated as part of the pre-requisites
    - make the "Full Name" the value of "Trello Key"
    - make the "First Name" the value of your first name
    - make the "Last Name" the value of your last name
    - save the new user
- Unzip the com.soa.pso.policy.Trello_1.0.0.zip file into the /sm70 directory of you ND installation(s). For Each ND:
    - restart your ND
    - loging to the ND Admin console
    - select the "Insert Trello Credentials Policy Handler" Policy in the "Avaialble Features" tab and follow the Wizard installation instructions

#### Verify Connectivity
- curl --user username:password http://"ND Servername and port"/trello/members/my/boards
    - where the username is the name of the PM user you defined in "Configure Security" and the password is that users password
    - where "ND Servername and port" is the URL for your ND 
    - /members/my/boards is the operation you want to call. In this case the list of boards the username is a member of
- The correct response for this example will be something like:
    [{"id":"54e3fa9c2e5d590f15428954",**"name":"API Hooks"**,"desc":"","descData":null,"closed":false,"idOrganization":null,"invited":false,"pinned":false,"starred":false,"url":"https://trello.com/b/iTokRjbx/api-hooks","prefs":{"permissionLevel":"private","voting":"disabled","comments":"members","invitations":"members","selfJoin":false,"cardCovers":true,"cardAging":"regular","calendarFeedEnabled":false,"background":"blue","backgroundColor":"#0079BF","backgroundImage":null,"backgroundImageScaled":null,"backgroundTile":false,"backgroundBrightness":"unknown","canBePublic":true,"canBeOrg":true,"canBePrivate":true,"canInvite":true},"invitations":[],"memberships":[{"id":"54e3fa9c2e5d590f15428955","idMember":"54e3f9fa069e76b6d6f77b8b","memberType":"admin","unconfirmed":false,"deactivated":false}],"shortLink":"iTokRjbx","subscribed":false,"labelNames":{"green":"","yellow":"","orange":"","red":"","purple":"","blue":"","sky":"","lime":"","pink":"","black":""},"powerUps":["calendar"],"dateLastActivity":"2015-02-18T02:53:53.021Z","dateLastView":"2015-02-18T08:30:16.924Z","shortUrl":"https://trello.com/b/iTokRjbx"},{"id":"54e3f9fa069e76b6d6f77b8c",**"name":"Welcome Board"**,"desc":"","descData":null,"closed":false,"idOrganization":null,"invited":false,"pinned":false,"starred":false,"url":"https://trello.com/b/gsDQd5o2/welcome-board","prefs":{"permissionLevel":"private","voting":"disabled","comments":"members","invitations":"members","selfJoin":true,"cardCovers":true,"calendarFeedEnabled":false,"background":"blue","backgroundColor":"#0079BF","backgroundImage":null,"backgroundImageScaled":null,"backgroundTile":false,"backgroundBrightness":"unknown","canBePublic":true,"canBeOrg":true,"canBePrivate":true,"canInvite":true},"invitations":[],"memberships":[{"id":"54e3f9fa069e76b6d6f77b8d","idMember":"4e6a7fad05d98b02ba00845c","memberType":"normal","unconfirmed":false,"deactivated":false},{"id":"54e3f9fb069e76b6d6f77b91","idMember":"54e3f9fa069e76b6d6f77b8b","memberType":"admin","unconfirmed":false,"deactivated":false}],"shortLink":"gsDQd5o2","subscribed":false,"labelNames":{"green":"","yellow":"","orange":"","red":"","purple":"","blue":"","sky":"","lime":"","pink":"","black":""},"powerUps":[],"dateLastActivity":"2015-02-18T02:33:31.215Z","dateLastView":null,"shortUrl":"https://trello.com/b/gsDQd5o2"}]

    which is the list of boards...in this case the two highlighted

### Modify and Build
In the event you need to change the API Hook.   Here are the instructions to do so. 

### License
Put a link to an open source license
