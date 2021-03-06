# Installation

## Requirements

In order to properly run Huddle, Git must be installed on the operating system.  In 
Windows environments, download and install the appropriate binary.  On Debian systems,
`apt install git` will usually do the trick.

## Install

Huddle may be installed using pip:

    pip install huddle 

This will work for most users in most environments.

The most recent revision may also be downloaded from the 
[github repository](https://github.com/slightlynybbled/huddle) and installed using 

    python setup.py install 

# Configuration

## Format

Huddle depends on configuration files to perform mosts tasks.  Configuration files are
in `.json` format.  Each file or application to be managed will have one corresponding
configuration file.

A simple example of a JSON configuration file would be:

    {
        "repository": {
            "remote path": "https://github.com/slightlynybbled/dummy.git",
            "local path": "/home/ubuntu/git_example"
        },
    }
    
or, if you prefer INI:

    [repository]
    remote path = https://github.com/slightlynybbled/dummy.git
    local path = /home/ubuntu/git_example

This configuration file would simply ensure that the local path files are always in
sync with the remote path files, which are located on the shown git repository.  Huddle 
will automatically sync the `local path` with the `remote path` repository.

See [config file format](configfiles.md) for more details regarding configuration
file settings and for examples.

## Location

All config files should reside in the same directory and have an extension of `.json`.
Any file prefixed with an underscore `_` will be ignored by huddle.

    - /home/ubuntu/config_files
      - /fileset0_config.json 
      - /app0_config.json 
      - /app1_config.ini 
      - /_app2_config.json 

The above file structure would work.  Note that the file structure is flat.  No files are
to be located in a subdirectory or they will not be parsed.  Note that the
`_app2_config.json` file would be ignored since it has a leading underscore `_`.

Files may be located anywhere on the file system to which huddle has access.

# Starting Huddle 

Once installed, huddle may be started by simply:

    huddle -c <config directory path>

or on a virtual environment named `py3env':

    ./py3env/bin/huddle -c <config directory path>

On the first instantiation, it may be necessary to add hosts to the ssh known_hosts 
so that the local machine recognizes remote git repositores without having to type
'yes' to accept new keys.
