---
title: "How do I remove Packages that Arnt in Package Manager?"
date: 2009-02-26
forum: General Help
---

### Post by orc_dragoon on 2009-02-26
How do I uninstall Packages like multiget and others that I downloaded that arnt in the Package Manager?

---

### Post by mb_webguy on 2009-02-26
How did you install them?  The only reason a program wouldn't be in the package manager would be if you compiled it yourself, or if it had an installer script.  With the latter, there's usually an uninstaller script, or an option for the installer script to uninstall the software.  

For the former, you have to go to the installation directory (i.e. the one containing the makefile you used to install the software) and type "sudo make uninstall".  If you deleted that directory, download it again, run configure and make to get the makefile just as you did the first time, then use that command.

Otherwise, you pretty much have to search through your filesystem for anything having to do with the program and delete it by hand.  Fortunately, Linux doesn't have anything like the Windows registry, so uninstalling a program is as simple as deleting it.

---

