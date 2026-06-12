---
title: "Kynaptic won't install programs"
date: 2005-08-03
forum: Desktop Environments
---

### Post by Thanatos Silentes on 2005-08-03
I'm new to kubuntu & i've managed to get it mostly working, but I'm having a problem with Kynaptic.  I've tried searching the forum but didn't find anything.
I'm trying to install Azureus using kynaptic.  I can tell it to install alright, and it comes up with the commit changes window.  I click OK, and it shows the message "building dependency tree".  It then goes back into the main window, and it hasn't installed azureus.  I've tried installing synaptic, but synaptic doesn't even get that far.  Any help would be appreciated.

---

### Post by drizek on 2005-08-03
[QUOTE=Thanatos Silentes]I'm new to kubuntu & i've managed to get it mostly working, but I'm having a problem with Kynaptic.  I've tried searching the forum but didn't find anything.
I'm trying to install Azureus using kynaptic.  I can tell it to install alright, and it comes up with the commit changes window.  I click OK, and it shows the message "building dependency tree".  It then goes back into the main window, and it hasn't installed azureus.  I've tried installing synaptic, but synaptic doesn't even get that far.  Any help would be appreciated.[/QUOTE]
 try apt-getting smartpm (need universe). can you install anything other than azureus? if so, just install azureus by hand, its very easy cause you dont need to compile anything.

---

### Post by Thanatos Silentes on 2005-08-04
When I try to install smartpm I get this:

bonk@hades:~$ sudo -H apt-get install smartpm
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  smartpm: Depends: python2.4-gtk2 but it is not installable
E: Broken packages

I've tried one or two other packages, and the same sort of thing happens.

---

### Post by drizek on 2005-08-04
Thats wierd. did you do anything to mess up kynaptic? 

i havent tried smart in kubuntu yet, but that same package worked fine in mepis. not really sure what to do now. maybe a reinstall?

---

### Post by Thanatos Silentes on 2005-08-04
I tried to install the package it  complained about and got this feedback:

bonk@hades:~$ sudo -H apt-get install python2.4-gtk2
Reading package lists... Done
Building dependency tree... Done
Package python2.4-gtk2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://82.211.81.138](http://82.211.81.138) hoary/main Packages (/var/lib/apt/lists/82.211.81.138_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package python2.4-gtk2 has no installation candidate

---

### Post by drizek on 2005-08-04
[QUOTE=Thanatos Silentes]I tried to install the package it  complained about and got this feedback:

bonk@hades:~$ sudo -H apt-get install python2.4-gtk2
Reading package lists... Done
Building dependency tree... Done
Package python2.4-gtk2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://82.211.81.138](http://82.211.81.138) hoary/main Packages (/var/lib/apt/lists/82.211.81.138_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package python2.4-gtk2 has no installation candidate[/QUOTE]
 google a deb for that package and see if you can install it with "dpkg -i"  in a terminal

---

### Post by Thanatos Silentes on 2005-08-04
This is the result:

bonk@hades:~$ sudo dpkg -i python2.4-gtk2_2.6.2-1.1_i386.deb
Password:
Selecting previously deselected package python2.4-gtk2.
(Reading database ... 58827 files and directories currently installed.)
Unpacking python2.4-gtk2 (from python2.4-gtk2_2.6.2-1.1_i386.deb) ...
dpkg: dependency problems prevent configuration of python2.4-gtk2:
 python2.4-gtk2 depends on libatk1.0-0 (>= 1.9.0); however:
  Package libatk1.0-0 is not installed.
 python2.4-gtk2 depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 python2.4-gtk2 depends on libgtk2.0-0 (>= 2.6.0); however:
  Package libgtk2.0-0 is not installed.
 python2.4-gtk2 depends on libpango1.0-0 (>= 1.8.1); however:
  Package libpango1.0-0 is not installed.
 python2.4-gtk2 depends on python-gtk2-common; however:
  Package python-gtk2-common is not installed.
dpkg: error processing python2.4-gtk2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-gtk2

---

