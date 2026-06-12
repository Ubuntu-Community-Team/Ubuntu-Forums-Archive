---
title: "XCHAT install"
date: 2007-01-09
forum: Desktop Environments
---

### Post by tylersontag on 2007-01-09
i tried to get xchat installed on my laptop but it says theirs a missing dependency of tcl8.4 not being up to date, however is not updateable. heres the aptitude printout

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xchat: Depends: tcl8.4 (>= 8.4.5) but it is not installable
E: Broken packages
$ sudo aptitude install xchat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  xchat 
The following NEW packages will be automatically installed:
  xchat-common 
The following NEW packages will be installed:
  xchat-common 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 965kB of archives. After unpacking 2773kB will be used.
The following packages have unmet dependencies:
  **xchat: Depends: tcl8.4 (>= 8.4.5) which is a virtual package.**
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
xchat [Not Installed]

Leave the following dependencies unresolved:
xchat-common recommends xchat
Score is -201

```

---

