Changelog
******************************

- **v0.10.0 (*2018-12-20*)**

  - Changed

    - ``PipelineInterface`` now derives from ``peppy.AttributeDict``.

    - On ``PipelineInterface``, iteration over pipelines now is with ``iterpipes``.

    - Rename ``parse_arguments`` to ``build_parser``, which returns ``argparse.ArgumentParser`` object

    - Integers in HTML reports are made more human-readable by including commas.

    - Column headers in HTML reports are now stricly for sorting; there's a separate list for plottable columns.

    - More informative error messages

  - Fixed

    - HTML samples list is fully populated.

    - Existence of an object lacking an anchor image is no longer problematic for ``summarize``.

    - Basic package test in Python 3 now succeeds: ``python3 setup.py test``.

- **v0.9.2** (*2018-11-12*):

  - Fixed

    - Fixed bugs with ``looper summarize`` when no summarizers were present

    - Added CLI flag to force ``looper destroy`` for programmatic access

    - Fixed a bug for samples with duplicate names

    - Added new display features (graphs, table display) for HTML summary output.


- **v0.9.1** (*2018-06-30*):

  - Fixed

    - Fixed several bugs with ``looper summarize`` that caused failure on edge cases.


- **v0.9.0** (*2018-06-25*):

  - New

    - Support for custom summarizers

    - Add ``allow-duplicate-names`` command-line options

    - Allow any variables in environment config files or other ``compute`` sections to be used in submission templates. This allows looper to be used with containers.

    - Add nice universal project-level HTML reporting


- **v0.8.1** (*2018-04-02*):

  - Changed

    - Minor documentation and packaging updates for first Pypi release.

    - Fix a bug that incorrectly mapped protocols due to case sensitive issues

    - Fix a bug with ``report_figure`` that made it output pandas code


- **v0.8.0** (*2018-01-19*):

  - Changed

    - Use independent `peppy` package, replacing ``models`` module for core data types.

    - Integrate ``ProtocolInterface`` functionality into ``PipelineInterface``.

- **v0.7.2** (*2017-11-16*):

  - Fixed
  
    - Correctly count successful command submissions when not using `--dry-run`.

- **v0.7.1** (*2017-11-15*):

  - Fixed
  
    - No longer falsely display that there's a submission failure.
      
    - Allow non-string values to be unquoted in the ``pipeline_args`` section.

- **v0.7** (*2017-11-15*):

  - New
      
    - Add ``--lump`` and ``--lumpn`` options
    
    - Catch submission errors from cluster resource managers
    
    - Implied columns can now be derived
    
    - Now protocols can be specified on the command-line `--include-protocols`
    
    - Add rudimentary figure summaries
    
    - Simplifies command-line help display
    
    - Allow wildcard protocol_mapping for catch-all pipeline assignment
    
    - Improve user messages
    
    - New sample_subtypes section in pipeline_interface
    
  - Changed
  
    - Sample child classes are now defined explicitly in the pipeline interface. Previously, they were guessed based on presence of a class extending Sample in a pipeline script.
    
    - Changed 'library' key sample attribute to 'protocol'

- **v0.6** (*2017-07-21*):

  - New

    - Add support for implied_column section of the project config file

    - Add support for Python 3

    - Merges pipeline interface and protocol mappings. This means we now allow direct pointers to ``pipeline_interface.yaml`` files, increasing flexibility, so this relaxes the specified folder structure that was previously used for ``pipelines_dir`` (with ``config`` subfolder).

    - Allow URLs as paths to sample sheets.

    - Allow tsv format for sample sheets.
  
    - Checks that the path to a pipeline actually exists before writing the submission script. 

  - Changed

    - Changed LOOPERENV environment variable to PEPENV, generalizing it to generic models

    - Changed name of ``pipelines_dir`` to ``pipeline_interfaces`` (but maintained backwards compatibility for now).

    - Changed name of ``run`` column to ``toggle``, since ``run`` can also refer to a sequencing run.

    - Relaxes many constraints (like resources sections, pipelines_dir columns), making project configuration files useful outside looper. This moves us closer to dividing models from looper, and improves flexibility.

    - Various small bug fixes and dev improvements.

    - Require `setuptools` for installation, and `pandas 0.20.2`. If `numexpr` is installed, version `2.6.2` is required.

    - Allows tilde in ``pipeline_interfaces``

- **v0.5** (*2017-03-01*):

  - New

    - Add new looper version tracking, with `--version` and `-V` options and printing version at runtime

    - Add support for asterisks in file paths

    - Add support for multiple pipeline directories in priority order

    - Revamp of messages make more intuitive output

    - Colorize output

    - Complete rehaul of logging and test infrastructure, using logging and pytest packages

  - Changed

    - Removes pipelines_dir requirement for models, making it useful outside looper

    - Small bug fixes related to `all_input_files` and `required_input_files` attributes
    
    - More robust installation and more explicit requirement of Python 2.7


- **v0.4** (*2017-01-12*):

  - New

    - New command-line interface (CLI) based on sub-commands

    - New subcommand (``looper summarize``) replacing the ``summarizePipelineStats.R`` script

    - New subcommand (``looper check``) replacing the ``flagCheck.sh`` script

    - New command (``looper destroy``) to remove all output of a project

    - New command (``looper clean``) to remove intermediate files of a project flagged for deletion

    - Support for portable and pipeline-independent allocation of computing resources with Looperenv.

  - Changed

    - Removed requirement to have ``pipelines`` repository installed in order to extend base Sample objects

    - Maintenance of sample attributes as provided by user by means of reading them in as strings (to be improved further)

    - Improved serialization of Sample objects
