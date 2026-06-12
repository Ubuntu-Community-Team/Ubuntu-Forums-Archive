---
title: "Installation Error (GDB, Bug-buddy etc)"
date: 2005-10-24
forum: Desktop Environments
---

### Post by austinz on 2005-10-24
Hello

I just performed a fresh install of Breezy from the ISO on ubuntulinux.com  The installation seemed to be going fine until the package installation portion, where at 84 percent I received an error saying not all packages were installed correctly, and maybe if I ran the installation part again the prolem would be fixed.  I click ok and the computer starts gnome just fine, I log in, etc.  I try to run synaptic, some packages are updated, but at the end there's three with "dependencies that are unresolved" .   I run sudo apt-get update and sudo apt-get upgrade and this message is printed:

```

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gdb (6.3-6ubuntu2) ...

gzip: stdin: invalid compressed data--crc error
install-info(/usr/share/info/gdb.info): read gzip -cd </usr/share/info/gdb.info.gz |: 256
dpkg: error processing gdb (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on gdb; however:
  Package gdb is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on bug-buddy; however:
  Package bug-buddy is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gdb
 bug-buddy
 ubuntu-desktop

```

Everything seems to be working well, but I wondered if there was any way to force these packages to configure or i\f anyone else has had a similar problem? 

By the way, I'm running:

800mhz AMD Duron
6** Meg RAM
10gb hard drive (unknown)
Generic Rage 128 Video
Creative Audigy soundcard

Thanks for the help!

Cheers
Austin

---

