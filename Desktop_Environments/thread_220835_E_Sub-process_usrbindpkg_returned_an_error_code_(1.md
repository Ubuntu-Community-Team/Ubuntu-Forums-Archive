---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2006-07-22
forum: Desktop Environments
---

### Post by abhiomkar on 2006-07-22
I tried to upgrade my dapper drake to edgy eft
(replacing all dapper to edgy in /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade)
some packages are failed to uprade
i restared my system, then xorg failed to start, no GUI.
(Iam posting this thread using links2 - command line browser)

I think some broken packages are there.
I tried "sudo apt-get -f install" also,
it is saying E: Sub-process /usr/bin/dpkg returned an error code (1)

Whenever i try apt-get it is saying error, lets say i want to install moon-buggy ...

abhinay@abhinay-desktop:~$ sudo apt-get install moon-buggy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  moon-buggy
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
2 not fully installed or removed.
Need to get 127kB of archives.
After unpacking 291kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe moon-buggy 1.0.51-1 [127kB]
Fetched 127kB in 47s (2704B/s)                                                 
Preconfiguring packages ...
Selecting previously deselected package moon-buggy.
(Reading database ... 130219 files and directories currently installed.)
Unpacking moon-buggy (from .../moon-buggy_1.0.51-1_i386.deb) ...
[B]Setting up acpid (1.0.4-5ubuntu3) ...
 * Loading ACPI modules...                                               [ ok ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Setting up moon-buggy (1.0.51-1) ...

Errors were encountered while processing:
 acpid
 acpi-support
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

every time same error.

Hw to solve this problem.

How to successfully upgrade my dapper drake to edgy eft.
Thank you.

---

### Post by unisol on 2006-07-22
try dpkg --configure -a also try sudo apt-get clean

---

### Post by SimonJW on 2006-07-22
The problem is that the package acpid has hit an error halfway through installation, and is now broken. Until this is fixed, no other packages can be installed or upgrade or anything, as the computer is first trying and failing to fix this broken package.

The problem occurs when the post-installation script tries to start the acpid process. Try starting it manually with
```
sudo /etc/init.d/acpid start
```
and report back on any error messages. If this seem to work, try running
```
sudo apt-get -f install
``` to see if you can now succesfully fix the broken package.

You can also try removing the suspect package with 
```
sudo apt-get remove acpid acpi-support
```
but I don't know how important this package is, and it may also need to remove tons of other things as well, in which case DON'T remove it as the other things may be important.

Let us know what happens!

---

