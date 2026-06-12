---
title: "im tying to install a few Dungeon crawler style games but i get an error every time"
date: 2009-08-09
forum: Gaming &amp; Leisure
---

### Post by ydoc1992 on 2009-08-09
here is the error

cody@Mac:~$ sudo apt-get install egoboo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  egoboo-data
The following NEW packages will be installed:
  egoboo egoboo-data
0 upgraded, 2 newly installed, 0 to remove and 41 not upgraded.
Need to get 0B/15.8MB of archives.
After this operation, 40.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package egoboo-data.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `stoneredition-theme-pack-2.0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
cody@Mac:~$ 

please help. and if it helps i tryed to remove to theme pack but i got an error doing that also.

---

### Post by Perfect Storm on 2009-08-11
Try first with;

```
sudo apt-get update && sudo apt-get upgrade
```

It might help to run this command to fresh the list up and update the stuff.
If you get the same error afterwards open synaptic package manager, click "Edit" tab and pick "Fix broken Packages".

If that doesn't help, please report back and lets see what else can be done.

---

