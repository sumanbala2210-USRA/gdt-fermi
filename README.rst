=========
GDT-Fermi
=========

The GDT-Fermi is an extension to Gamma-ray Data Tools that adds functions specific to the Fermi mission (GBM and LAT).

The full documentation can be found `here <https://astro-gdt.readthedocs.io/projects/astro-gdt-fermi/en/latest/>`_.

This software is not subject to EAR.

Normal Installation
-------------------

If you don't plan to contribute code to the project, the recommended install method is installing from PyPI using:

.. code-block:: sh

   pip install astro-gdt-fermi
   gdt-data init

The ``gdt-data init`` is required to initialize the library after installation of astro-gdt. You do not need to
perform the initialization again if astro-gdt was already installed and initialized.  There is no harm in running
it again "just in case".


Setting up a development environment
------------------------------------

If you do want to contribute code to this project (and astro-gdt), you can use the following commands to quickly setup a
development environment:

.. code-block:: sh

   mkdir gdt-devel
   cd gdt-devel
   python -m venv venv
   . venv/bin/activate
   pip install --upgrade pip setuptools wheel
   git clone git@github.com:sumanbala2210-USRA/gdt-core.git
   git clone git@github.com:sumanbala2210-USRA/gdt-fermi.git
   pip install -e gdt-core/
   pip install -r gdt-core/requirements.txt
   gdt-data init
   pip install -e gdt-fermi/
   pip install -r gdt-fermi/requirements.txt

This should result in git-devel having the following directory structure::

   .
   ├── venv
   ├── gdt-core
   └── gdt-fermi

and both gdt-core and gdt-fermi installed in the virtual environment named venv.

Writing Extensions using Namespace Packaging
--------------------------------------------
Gamma-ray Data Tools encourages missions to write extensions using namespace packages. Please use our
`Fermi extension <https://github.com/USRA-STI/gdt-fermi>`_ as an example of how we expect other missions to contribute
extensions to the Gamma-ray Data Tools.

The extension package should contain a directory 'gdt' with a subdirectory 'missions' which will hold the extension code
in a package directory named after the mission.

For example, GDT-Fermi has the following directory layout::

  .
  ├── config
  ├── dist
  ├── docs
  ├── src
  │   └── gdt
  │      └── missions
  │          └── fermi
  │              ├── gbm
  │              │   └── __init__.py
  │              ├── lat
  │              │   └── __init__.py
  │              └── __init__.py
  └── tests
    └── missions
        └── fermi


Since GDT-Fermi uses namespace packaging, both ``src/gdt`` and  ``src/gdt/missions`` do not contain a file named
``__init__.py``. This is because they are Namespace packages.

Notice that directory ``src/gdt/mission/fermi`` and its subdirectories contains an `__init__.py` file
signalling to Python that those directories are regular packages.

You can learn more about Namespace packages by reading `PEP-420 <https://peps.python.org/pep-0420/>`_.

Helping with Documentation
--------------------------

You can contribute additions and changes to the documentation. In order to use sphinx to compile the documentation
source files, we recommend that you install the packages contained within ``requirements.txt``.

To compile the documentation, use the following commands:

.. code-block:: sh

   cd gdt-fermi/docs
   make html

