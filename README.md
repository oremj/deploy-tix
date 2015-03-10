deploy-tix
=============

Python scripts to generate Bugzilla deployment tickets for Mozilla Services.

Still under heavy development. FOR OPS USE AND DEMO ONLY.

## Projects
 * loop-server
 * loop-client
 * msisdn-gateway
 * shavar
 * pushgo

## Setup
deploy-tix will make multiple calls to github API.
You're allowed up to 60 calls / hour without authentication, but you'll soon
run out!

Instead, create an access token from your github home page.  Go to:

 - Settings > Applications > Generate New Token
 - Create an environment variable 'ACCESS_TOKEN' or enter it into the config.py:
   `$ export ACCESS_TOKEN=<your_access_token_here>`
 - Build and run:
 - `$ make build`
 - `$ source ./build/venv/bin/activate`


## Options
 ```sh
(venv)$ ticket -h
usage: ticket [-h] [-o REPO_OWNER] -r REPO [-e ENVIRONMENT] -u
              BUGZILLA_USERNAME -p BUGZILLA_PASSWORD [-z]

Scripts for creating / updating deployment tickets in Bugzilla

optional arguments:
  -h, --help            show this help message and exit
  -o REPO_OWNER, --repo-owner REPO_OWNER
                        Example: mozilla-services (default: mozilla-services)
  -r REPO, --repo REPO  Example: loop-server (default: None)
  -e ENVIRONMENT, --environment ENVIRONMENT
                        Enter: STAGE, PROD (default: STAGE)
  -u BUGZILLA_USERNAME, --bugzilla-username BUGZILLA_USERNAME
  -p BUGZILLA_PASSWORD, --bugzilla-password BUGZILLA_PASSWORD
  -z, --bugzilla-prod   Add this option, and you'll post to bugzilla prod
                        (default: False)
 ```

## Example
  - Post to bugzilla-dev
    `$ ticket -h -r mozilla-services -a loop-server -e STAGE -u johnny@quest.com -p password123`

  - Post to bugzilla (add -z option)
    `$ ticket -h -r mozilla-services -a loop-server -e STAGE -u johnny@quest.com -p password123 -z`

