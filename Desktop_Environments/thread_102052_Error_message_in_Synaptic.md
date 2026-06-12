---
title: "Error message in Synaptic"
date: 2005-12-11
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-11
I've posted this before, but the answer I got didn't lead anywhere:

I got a broke package: xmms-musepack. When trying to reinstall it I get:
E: /var/cache/apt/archives/libmpcdec3_1.2-1_i386.deb: trying to overwrite `/usr/lib/libmpcdec.so.3.0.0', which is also in package libmpcdec

Then I tried to remove that package, and here's what happened:

gabriel@ubuntu:~$ sudo apt-get remove libmpcdec
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gabriel@ubuntu:~$ sudo apt-get remove libmpcdec
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  xmms-musepack: Depends: libmpcdec3 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
gabriel@ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
gabriel@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmpcdec3
The following NEW packages will be installed:
  libmpcdec3
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
6 not fully installed or removed.
Need to get 0B/25.0kB of archives.
After unpacking 123kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libmpcdec3
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 117157 files and directories currently installed.)
Unpacking libmpcdec3 (from .../libmpcdec3_1.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmpcdec3_1.2-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmpcdec.so.3.0.0', which is also in package libmpcdec
Errors were encountered while processing:
 /var/cache/apt/archives/libmpcdec3_1.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
gabriel@ubuntu:~$

Why?

Thanx

Gabriel

---

### Post by aysiu on 2005-12-11
[QUOTE=GabrielWolff]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/QUOTE] I don't know about the other errors, but I usually get this one when I'm trying to apt-get while Synaptic is open.

---

### Post by GabrielWolff on 2005-12-11
[QUOTE=aysiu]I don't know about the other errors, but I usually get this one when I'm trying to apt-get while Synaptic is open.[/QUOTE]

Yeah, but I close it, and continued. Any clue what happened later on? Why can't I delet the package?

---

