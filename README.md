# Gitcentral

[![Build Status](https://drone.io/github.com/chuck211991/gitcentral/status.png)](https://drone.io/github.com/chuck211991/gitcentral/latest)
[![Coverage Status](https://coveralls.io/repos/github/chuck211991/gitcentral/badge.svg?branch=master)](https://coveralls.io/github/chuck211991/gitcentral?branch=master)
[![Documentation Status](https://readthedocs.org/projects/gitcentral/badge/?version=latest)](http://gitcentral.readthedocs.org/en/latest/?badge=latest)

This project aims to create an open-source implementation similiar to the very excellent Github.
The need for this is justified merely by the success of Github, which has done a wonderful job of unifying communities and providing a central location for projects to store their codebase, documentation, and issues.
However, despite facilitating open-source development, Github is not open-source.

Documentation can be found here: http://gitcentral.readthedocs.org/en/latest/

## Current Features

Gitcentral currently:
- Allows repository creation using a web interface; supporting both public and private repositories
- Has a simple framework to handle permissions on repositories
- Allows forking of repositories
- Has a simple file browser which supports branches
- Has a custom SSH server which limits permissions according the permission defined in the web interface
- Allows users to provide SSH keys which can be used to authenticate themselves

## Wanted Features

It would be great if we had...
- Pull requests
- Wiki's
- Issue trackers

## Getting started with development

To begin developing on this project, install python-virtualenv and configure the environment

For Ubuntu, execute the following after cloning the repository:
Only run these commands when setting up a machine for the first time

    # RUNONCE
    sudo apt-get install python-virtualenv
    sudo apt-get build-dep python-twisted

    # Setup the SSH-keys that will be used by the server
    ssh-keygen -t rsa -f id_rsa -N ''
    echo -n 'SERVER_PUBLIC_KEY = """' > local_settings.py
    cat id_rsa.pub >> local_settings.py
    echo -n -e "\"\"\"\n\nSERVER_PRIVATE_KEY = \"\"\"" >> local_settings.py
    cat id_rsa >> local_settings.py
    echo -e "\"\"\"" >> local_settings.py

Run these commands everytime

    # Everytime you begin development, before starting the server
    . ./activate
    # Sync the database
    python manage.py migrate

    # Run the server
    python manage.py runserver
    # And in a seperate terminal
    python manage.py git_server

### Other useful commands

    python manage.py test
    # Runs the unit tests
