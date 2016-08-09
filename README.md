
## Alexa Skill hosted within a webtask

This is a simple Alexa Service based on the Alexa Samples available at https://github.com/amzn/alexa-skills-kit-js/tree/master/samples/historyBuff

This code has been ported to be hosted within a webtask. 

## Concepts
- Hosting Alexa Skill in a webtask - This sample shows how to create a Webtask for handling Alexa Skill request that talks to an external wiki webservice to get details about what happend on a particualr day.
- Account Linking - The webtask is invoked to respond to alexa commands and also sends a user token as part of the session within the context. This token is an access_token issued by Auth0 and is used to allow/deny access

## Setup
To run this example skill you need to do two things. The first is to deploy this code in webtaks, and the second is to configure the Alexa skill to use this service

### Webtask setup
1. Go to https://webtask.io/cli and install the webtask cli and initialize it 
2. Download the file `historyBuff.js` and `AlexaSkill.js` to a folder
3. Create a new folder `build` within this folder
4. Run `wt-bundle --output build/historyBuff.js historyBuff.js` to build the webtask
5. `cd build`
6. Create the webtask`wt create historyBuff.js -s api_signing_secret=<api_signing_key>` - where api_signing_key is the signing key for the `History Buff API` - API defined within Auth0 - 
7. Copy the url for the webtask and use this url as the Endpoint within the Configuration section during the Alexa Skill Setup

## Examples
Example user interactions:

### One-shot model:
    User:  "Alexa, ask History Buff what happened on August thirtieth."
    Alexa: "For August thirtieth, in 2003, [...] . Wanna go deeper in history?"
    User:  "No."
    Alexa: "Good bye!"

### Dialog model:
    User:  "Alexa, open History Buff"
    Alexa: "History Buff. What day do you want events for?"
    User:  "August thirtieth."
    Alexa: "For August thirtieth, in 2003, [...] . Wanna go deeper in history?"
    User:  "Yes."
    Alexa: "In 1995, Bosnian war [...] . Wanna go deeper in history?"
    User:  "No."
    Alexa: "Good bye!"
