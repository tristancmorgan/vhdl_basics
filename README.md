# Quickstart Guide

This repo contains VHDL examples and associated tests. It's intended to provide an environment for testing FPGA candidates.

## Step 1: Environment setup

This repo is intended to be run on some flavour of Linux. I do most of my dev work on Ubuntu at the moment.

### Python environment

* Create a new python venv: `python3 -m venv venv`
* Activate your new environment: `source venv/bin/activate`
* Install the required packages from `requirements.txt`: `pip install -r tools/requirements.txt`

### Install a simulator

* Install GHDL (an open source VHDL simulator) through your package manager:
    * On ubuntu and debian systems this would be `sudo apt-get install ghdl`
    * On archlinux-based distros there is a package in the aur

## Step 2: Run a test

The entry point for all tests is through `pytest` (https://docs.pytest.org/en/7.1.x/contents.html) which can be run from the top level of this repo. 
Some useful `pytest` basics:
* `pytest --collect-only`: just find all the tests and print a list
* `pytest -k "<EXPRESSION>"`: run all tests whose name matches `EXPRESSION`. e.g. `pytest -k "pipe"`

## Step 3: Create a new module and testbench

* Copy `reg_stage.vhd` and `test_reg_stage.py` either just next to where they are in the `examples` top-level-dir or to the `src` top-level-dir. Give them a name that reflects your new module's purpose, depending on the task you've been given by the tester.
* Update the name of the your new module in the `*.vhd` file you just copied. Make it the same as the filename, without the `.vhd` extension.
* Update the name of the test function and all the paths, DUT names, and module references in the `*.py` test file you just copied (just search for `reg_stage` and you should find all the places that need to change)
* Run your new test on your new module to make sure all the plumbing is in place: `pytest -k "<your_test_name>`
* Start implementing actual new functionality and tests!
