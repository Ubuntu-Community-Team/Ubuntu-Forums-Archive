---
title: "Package manager errors"
date: 2006-01-13
forum: General Help
---

### Post by mdh on 2006-01-13
Hi breezy users,

Everytime I install/upgrade packages through apt-get or its front-end synaptic I get these error messages

[I]Setting up gs-esp (7.07.1-9ubuntu5) ...
/usr/share/doc-base/gs-esp: cannot open control file for reading: No such file or directory
dpkg: error processing gs-esp (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gs-esp; however:
  Package gs-esp is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gs-esp
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/I]

It looks like it is some kind of printing related package, I am not going to be using a printer with my PC. Is there a way for me to tell apt-get (synaptic) to ignore this package rather than report error messages every time I try to upgrade.

Thanks,
Murali.

---

### Post by Sef on 2006-01-13
You could have some broken packages.  To fix them do this:  System ----> Administration ----> Synaptic Package Manager -----> Edit ------> Fix Broken Packages.  And just follow the directions.  Mostly just clicking on either ok or yes.  
 Hope that fixes your problem.

---

