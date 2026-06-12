---
title: "rox-all 1.3 installation attempt and python-central problem"
date: 2008-11-11
forum: Desktop Environments
---

### Post by gilbertt on 2008-11-11
Tried to install rox-all 1.3 package on my Ubuntu system...this happened:

$ sudo dpkg -i Ubuntu/zeroinstall-injector_0.29-0ubuntu1_all.deb
Password:
Selecting previously deselected package zeroinstall-injector.
(Reading database ... 133221 files and directories currently installed.)
Unpacking zeroinstall-injector (from .../zeroinstall-injector_0.29-0ubuntu1_all.deb) ...
dpkg: dependency problems prevent configuration of zeroinstall-injector:
zeroinstall-injector depends on python-central (>= 0.5.6ubuntu2); however:
Package python-central is not installed.
dpkg: error processing zeroinstall-injector (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
zeroinstall-injector
[email]chelly@chelly-desktop:~/.flux[/email]box/rox-all-1.3/0launch$ sudo apt-get install python-central
Reading package lists... Done
Building dependency tree... Done
Package python-central is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-central has no installation candidate
[email]chelly@chelly-desktop:~/.flux[/email]box/rox-all-1.3/0launch$

I tried sudo apt-get install python-central:

$ sudo apt-get install python-central
Reading package lists... Done
Building dependency tree... Done
Package python-central is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-central has no installation candidate

So then opened Synaptic package manager but python-central isn't listed. There is a massive list of python packages listed, but there is no indication which if any of these I should install.

Finally went here:

[http://packages.ubuntu.com/feisty/al...ntral/download](http://packages.ubuntu.com/feisty/al...ntral/download)

to download the python-central package directly. It was a .deb file, which I tried to open with the 'GDebi Package Installer', but I got the error message 'Conflicts with the installed package 'debhelper'.

Can someone help?

---

### Post by gilbertt on 2008-11-11
Sod it. I found Rox-Filer in the Synaptic Package Manager

---

