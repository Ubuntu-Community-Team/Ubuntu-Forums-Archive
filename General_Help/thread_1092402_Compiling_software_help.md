---
title: "Compiling software help"
date: 2009-03-10
forum: General Help
---

### Post by pwebguy on 2009-03-10
I am testing some software on a project server, and am compiling the software for each test.

Currently I am reinstalling ubuntu and compiling the test software each time I preform a test. The reason is that I want to be 100% sure that all configuration files are rewritten fresh for each test.

If I simply re-compile and install the software does it typically rewrite all necessary config files and direcrories as new, or does it keep parts of the old install? In other words, is reinstalling the OS each time really necessary?

---

### Post by geraldm on 2009-03-11
It would depend upon what the permissions of the installed files are.
Normal would be that all files would be installed, overwriting any from a 
previous install.  The directories would remain from the previous install.
If you want 100% sure, you would uninstall the old package first.
By "reinstalling the OS" you just mean the package, not the OS.

A better way would be to create an object, or binary package.  Then remove the old package, and untar the package for the install.  There should be no need to
recompile unless the package source is to be changed.

regards,
Gerald

---

### Post by kevdog on 2009-03-11
Can you just uninstall the previous version (sudo make uninstall) rather than installing the OS over again?

---

