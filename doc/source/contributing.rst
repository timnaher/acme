.. Copyright © 2023 Ernst Strüngmann Institute (ESI) for Neuroscience
.. in Cooperation with Max Planck Society

.. SPDX-License-Identifier: CC-BY-NC-SA-1.0

Contributing to ACME
====================

We always welcome contributions to ACME! If you want to extend or modify
ACME, please don't hesitate to get in touch via our
`GitHub Issue Tracker <https://github.com/esi-neuroscience/acme/issues>`_.
We're looking forward to hearing from you!

.. contents:: Quick Links
    :depth: 3

Development Setup
-----------------

You want to work on ACME? Great! Simply follow the steps below to get up
and running (the instructions assume you are working on Linux/macOS - if
you want to set up a Windows environment )

1. Fork the ACME repo on GitHub as explained in `Fork a repo <https://docs.github.com/en/get-started/quickstart/fork-a-repo>`_
2. Clone your shiny new fork on your local machine (or cluster node):

   .. code-block:: shell

       git clone git://github.com/<your-github-profile>/acme.git
       cd acme

3. Create a fresh conda environment for ACME:

   .. code-block:: shell

       conda env create -f acme.yml

4. Activate the environment and run ACME's test-suite to ensure your system
   is set up correctly

   .. tabs::

       .. tab:: Linux/macOS

           .. code-block:: shell

               cd tests/
               ./run_tests.sh pytest

       .. tab:: Windows

           .. code-block:: shell

               cd tests/
               run_tests.cmd pytest

5. If everything looks fine, install ACME in "editable" mode. This creates
   a symlink to your local git repo in your environment's ``site-packages``
   directory (so you can import acme is if it was statically installed via
   pip)

   .. code-block:: shell

       cd ../
       pip install -e .

Congratulations, you're now ready to start tweaking ACME!

Development Pipeline
--------------------

We use feature branches for development with a dedicated development branch
``[dev]`` used to collect all "production-ready" features ahead of an upcoming
release.
To get your feature included in ACME's upstream code, please create a new
branch from ``[dev]`` in your fork and push your work to this branch. Once
you're done with your changes, please open a
`pull request <https://github.com/esi-neuroscience/acme/pulls>`_
for merging in the ``[dev]`` branch of ACME's
`main repository <https://github.com/esi-neuroscience/acme>`_.

Coding Style
-------------

ACME generally follows the `PEP 8 Style Guide <https://peps.python.org/pep-0008/>`_
and uses the `NumPy-Doc <https://numpydoc.readthedocs.io/en/latest/format.html>`_
conventions to format docstrings.

To keep commit logs transparent, we are using three-letter tags to
classify commit messages:

* **FIX** bugfix commit
* **CHG** change(s) in functionality
* **NEW** feature addition(s)
* **REM** feature/functionality removed
* **WIP** work-in-progress commit, code not yet functional
* **DOC** modifications in documentation

Each commit should ideally only use a single tag, specifically, please
try to not mix feature additions (NEW) and bugfixes (FIX). To add context
to a commit message, we use git's command line interface for committing
and simply un-comment the auto-generated "Changes to be committed" section.
To further help others retrace our steps, we usually refer to GitHub issues
by their number prepended with the "#" symbol. Here's an example:

.. code-block:: bash

    FIX: Addresses bug in this_function

    - the problem was fixed by doing something incredibly smart
      in `this_function`
    - in the process another bug was fixed too
    - closes #4

    Changes to be committed:
        modified:   path/to/file1
        modified:   path/to/file2

Changelog
---------

We keep track of changes in ACME by keeping a global changelog inspired
by `Keep a Changelog <https://keepachangelog.com>`_. The structure of
ACME's changelog follows the exemplary layout below:

.. code-block:: bash

    # Changelog of ACME
    All notable changes to this project will be documented in this file.
    The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)

    ## [Unreleased]
    ### NEW
    ### CHANGED
    - Updated documentation

    ### REMOVED
    ### DEPRECATED
    ### FIXED
    - repaired bug in `this_function` (closes #4)


    ## [0.0.1] - 2023-03-01
    Bugfix release.

    ### CHANGED
    - Updated `this_function`

Feel free to add a short summary of your changes in the appropriate sections
under `[Unreleased]`.
