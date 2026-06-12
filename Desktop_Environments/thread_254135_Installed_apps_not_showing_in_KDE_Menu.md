---
title: "Installed apps not showing in KDE Menu"
date: 2006-09-09
forum: Desktop Environments
---

### Post by TheCelloFellow on 2006-09-09
Quick details: Kubuntu 6.06.1, nothing fancy.

If I try installing something, it doesn't appear in the KDE Menu. But, I also get these weird error messages about global destruction that have something to do with QT.

```
josh@josh-desktop:~$ sudo aptitude install linneighborhood
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  smbfs
The following NEW packages will be installed:
  linneighborhood smbfs
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/553kB of archives. After unpacking 1602kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
**DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 2 during global destruction.**
Selecting previously deselected package smbfs.
(Reading database ... 89366 files and directories currently installed.)
Unpacking smbfs (from .../smbfs_3.0.22-1ubuntu3.1_i386.deb) ...
Selecting previously deselected package linneighborhood.
Unpacking linneighborhood (from .../linneighborhood_0.6.5-3.1_i386.deb) ...
Setting up smbfs (3.0.22-1ubuntu3.1) ...
Setting up linneighborhood (0.6.5-3.1) ...

```
After the install, I manually run kbuildsycoca to add the apps to the meny and get this error.

```
josh@josh-desktop:~$ kbuildsycoca
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
```


I don't know if the errors are realated, but they seemed to both start happening the same time. I asked about the global destruction stuff on the Kubuntu IRC channel and no one knew what it was.

---

### Post by TheCelloFellow on 2006-09-09
Hello? Anybody there?

---

### Post by TheCelloFellow on 2006-09-10
Hello? Anybody there? :confused:

---

### Post by a_hippie on 2006-10-09
Greetings TheCelloFellow

I'm currently running into the very same issue.  One beef was google.earth.  I removed it, but still I get the same problem.

I can not alter or add things to startup menu.  wapita!

I'll keep digging.

Did you post this issue on kubuntu formum?

Thanks!

Wishing you well.

---

### Post by TheCelloFellow on 2006-10-09
Well, I've since reinstalled (accidently copied a floppy image to /dev/hda1 :$), but I found out that if you have your panels locked the KDE Menu is locked too. So, whenever you run apt-get, aptitude, or Adept, make sure you have unlocked your panel or nothing will appear when you install. If you do accidently install with a locked panel, then unlock them and run kbuilsycoca. :-)

---

