# How to Install Python packages from Azure Artifacts

## Steps

The simpler and more intuitive way is:

1. Prepare 2 requirements.txt files.

   * The first one `requirements-0-azure-artifacts-prerequisite.txt`
     is already prepared for you in this repo.
     It contains the prerequisite tools. You shall use it as-is.
   * The second one `requirements-1-azure-artifacts.txt`
     shall contain the index url of your Azure Artifact,
     and the actual packages that your project needs to use.
     This repo provides an example for using a non-public MISE package.

2. Use TWO pip install commands,
   `pip install -r requirements-0-azure-artifacts-prerequisite.txt`
   and `pip install -r requirements-1-azure-artifacts.txt`
   to install them.
   And your package is now available in your local environment.

3. [Optional] If you happen to also use
   [tox](https://tox.wiki/en/latest/index.html) in your project,
   this repo also contains a `tox.ini` so that you can simply
   use `tox` to prepare your environment,
   and use `tox -- python -c "import your_package"` to verify its readiness.


## Appendix: The alternative method that is not used by this repo

The official instruction in the
[Connect to a feed](https://learn.microsoft.com/en-us/azure/devops/artifacts/quickstarts/python-packages?view=azure-devops&tabs=pip#connect-to-a-feed)
can work.
However, its step 4, 5, 6 are atypical of normal Pythonic approaches.

* The "Get the tools" prerequisites need to be installed BEFORE attempting
  to install the packages hosted in Azure Artifacts
* Virtual environment is good but not strictly necessary
* Manually adding a `pip.ini` or `pip.conf` is troublesome.

So, this repo goes with a different approach.
