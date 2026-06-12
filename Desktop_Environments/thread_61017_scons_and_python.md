---
title: "scons and python"
date: 2005-08-30
forum: Desktop Environments
---

### Post by salladen on 2005-08-30
Since I was unable to get scons via apt-get I downloaded scons_0.96.1-0.1_all.deb from their site. But when I am trying to install it I get this :
```

                         :~$ sudo dpkg -i scons_0.96.1-0.1_all.deb
Selecting previously deselected package scons.
(Reading database ... 56708 files and directories currently installed.)
Unpacking scons (from .../scons_0.96.1-0.1_all.deb) ...
dpkg: dependency problems prevent configuration of scons:
 scons depends on python2.2; however:
  Package python2.2 is not installed.
dpkg: error processing scons (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 scons

```
scons doesnt seem to work with python2.3 or 2.4  ??

anyway.. tryed to install python2.2_2.2.3dfsg-2_i386.deb instead : 
```

                     :~$ sudo dpkg -i python2.2_2.2.3dfsg-2_i386.deb
Selecting previously deselected package python2.2.
(Reading database ... 56858 files and directories currently installed.)
Unpacking python2.2 (from .../python2.2_2.2.3dfsg-2_i386.deb) ...
dpkg: dependency problems prevent configuration of python2.2:
 python2.2 depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
dpkg: error processing python2.2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.2

```
so i tryed :
```

                       :~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Then what? Help please.
What to do with libc6 ?

Thankful for any help given.

---

### Post by arnieboy on 2005-08-30
[QUOTE=salladen]Since I was unable to get scons via apt-get I downloaded scons_0.96.1-0.1_all.deb from their site. But when I am trying to install it I get this :
```

                         :~$ sudo dpkg -i scons_0.96.1-0.1_all.deb
Selecting previously deselected package scons.
(Reading database ... 56708 files and directories currently installed.)
Unpacking scons (from .../scons_0.96.1-0.1_all.deb) ...
dpkg: dependency problems prevent configuration of scons:
 scons depends on python2.2; however:
  Package python2.2 is not installed.
dpkg: error processing scons (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 scons

```
scons doesnt seem to work with python2.3 or 2.4  ??

anyway.. tryed to install python2.2_2.2.3dfsg-2_i386.deb instead : 
```

                     :~$ sudo dpkg -i python2.2_2.2.3dfsg-2_i386.deb
Selecting previously deselected package python2.2.
(Reading database ... 56858 files and directories currently installed.)
Unpacking python2.2 (from .../python2.2_2.2.3dfsg-2_i386.deb) ...
dpkg: dependency problems prevent configuration of python2.2:
 python2.2 depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
dpkg: error processing python2.2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.2

```
so i tryed :
```

                       :~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Then what? Help please.
What to do with libc6 ?

Thankful for any help given.[/QUOTE]
go to synaptic and search for python2.2 (dont try to install the debian deb which u downloaded from somewhere) and install that
that might do the trick for u.

---

### Post by salladen on 2005-08-30
thanks arnie. that did it.   :)

---

### Post by arnieboy on 2005-08-30
[QUOTE=salladen]thanks arnie. that did it.   :)[/QUOTE]
glad I could help :)

---

