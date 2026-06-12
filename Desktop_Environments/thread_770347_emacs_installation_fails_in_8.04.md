---
title: "emacs installation fails in 8.04"
date: 2008-04-27
forum: Desktop Environments
---

### Post by schallstrom on 2008-04-27
When I try to install emacs on a fresh Ubuntu 8.04 installation I get the following error. I tried to purge all packages involving emacs again and running "aptitude autoclean" and "aptitude clean" and install again, same error. I also found some related bug reports on launchpad but no solution. What can I do?

```

root@molniya:~# aptitude install emacs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  emacs22-bin-common emacs22-common emacs22-gtk emacsen-common 
The following NEW packages will be installed:
  emacs emacs22-bin-common emacs22-common emacs22-gtk emacsen-common 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/20.7MB of archives. After unpacking 64.9MB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Selecting previously deselected package emacsen-common.
(Reading database ... 100488 files and directories currently installed.)
Unpacking emacsen-common (from .../emacsen-common_1.4.17_all.deb) ...
Selecting previously deselected package emacs22-common.
Unpacking emacs22-common (from .../emacs22-common_22.1-0ubuntu10_all.deb) ...
Selecting previously deselected package emacs22-bin-common.
Unpacking emacs22-bin-common (from .../emacs22-bin-common_22.1-0ubuntu10_i386.deb) ...
Selecting previously deselected package emacs22-gtk.
Unpacking emacs22-gtk (from .../emacs22-gtk_22.1-0ubuntu10_i386.deb) ...
Selecting previously deselected package emacs.
Unpacking emacs (from .../emacs_22.1-0ubuntu10_all.deb) ...
Setting up emacsen-common (1.4.17) ...
emacsen-common: Handling install of emacsen flavor emacs

Setting up emacs22-common (22.1-0ubuntu10) ...

Setting up emacs22-bin-common (22.1-0ubuntu10) ...

Setting up emacs22-gtk (22.1-0ubuntu10) ...
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs22 failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs22
!! and attach the file /tmp/emacs22.Ag8018
dpkg: error processing emacs22-gtk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs22-gtk | emacs22 | emacs22-nox; however:
  Package emacs22-gtk is not configured yet.
  Package emacs22 is not installed.
  Package emacs22-gtk which provides emacs22 is not configured yet.
  Package emacs22-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs22-gtk
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up emacs22-gtk (22.1-0ubuntu10) ...
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs22 failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs22
!! and attach the file /tmp/emacs22.di8047
dpkg: error processing emacs22-gtk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs22-gtk | emacs22 | emacs22-nox; however:
  Package emacs22-gtk is not configured yet.
  Package emacs22 is not installed.
  Package emacs22-gtk which provides emacs22 is not configured yet.
  Package emacs22-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs22-gtk
 emacs
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

```

---

### Post by kelean on 2008-04-27
One thing you can try is this. 
```
#sudo apt-get -f install
```

Try that and see if it helps.  I have used that in the past.

---

### Post by jconstantino on 2008-05-01
> **kelean said:**
> One thing you can try is this. 
```
#sudo apt-get -f install
```

Try that and see if it helps.  I have used that in the past.


I have the same problem (upgrade from 7.10 to 8.04)
Your sugestion didn't worked for me...Do you have any suggestion?
Thanks in advance...

Error in:
 emacs22
 cedet-common
 eieio
 speedbar

---

### Post by jconstantino on 2008-05-09
> **jconstantino said:**
> I have the same problem (upgrade from 7.10 to 8.04)
Your sugestion didn't worked for me...Do you have any suggestion?
Thanks in advance...

Error in:
 emacs22
 cedet-common
 eieio
 speedbar

I have exactly the same problem! The sugestion above didn't worked for me either...
Any clue? Thanks in advance

---

