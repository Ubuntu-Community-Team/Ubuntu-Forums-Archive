---
title: "Salome 5.1.2 on jaunty amd64"
date: 2009-08-20
forum: Education &amp; Science
---

### Post by bobbish260 on 2009-08-20
I installed "complete version for Debian etch 64bit" of Salome to Ubuntu jaunty amd64 by runInstall batch mode, i.e. "./runInstall -b".

The message appeared when installing it as followings.
...............
>>> ... processing HXX2SALOMEDOC ...
It's impossible to install HXX2SALOMEDOC_5.1.2 from binaries
..........
>>> Creating environment files
/home/<user_name>/salome_appli_5.1.2 directory already exists, nothing done
/home/<user_name>/InstallWizard_5.1.2_Debian_4.0_64bit/config_files/KERNEL.sh: line 145: create_config.sh: command not found
>>> Check existence of Fortran and other required libraries...
=== WARNING: Some libraries are absent! ===
One or several MANDATORY libraries listed below are not found. SALOME may not work properly.
    libgfortran.so.1
One or several OPTIONAL libraries listed below are not found. This does not affect on the correct work of SALOME platform.
    libBLSurf.so
    libcppunit-1.12.so.0
>>> Cleaning temporary directory
>>> Finished!

Salome GUI can be launched, but some python script from "Salome user section" shows an error message about lacking of libgfortran.so.1.

Though the difference between version 4.1 and 4.2 is described in What's new in gfortran?" at "GNU gfortran wiki", I can't decide whether I can ignore the differences.

I would like to know what should I do for libgfortran.so.1.
Can I install old stable version of gfortran-4.1?
Can I link libgfortran.so.1 as symbolic link to libgfortran.so.2?
Should I compile libgfortran-4.1 from source cord?

---

### Post by Xnst on 2009-08-26
I recommend you to try to link libgfortran.so.1 to libgfortran.so.2. If it does not work just delete libgfortran.so.1 and all should be fine :). 

When I am in similar troubles with libraries, I use that workaround. Often the base library, lib---.so, is somewhere else and linked to from all lib---.so.x .

---

