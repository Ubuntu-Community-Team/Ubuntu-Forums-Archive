---
title: "how to remove compiz, apt-get confused"
date: 2007-09-18
forum: Desktop Environments
---

### Post by mega on 2007-09-18
Trying to remove beryl/emerald/compiz to set up compiz-fusion

I'm stuck in dependency hell, I cant get this thing off my machine!


mega@mainpc:~$ sudo apt-get remove compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  desktop-effects: Depends: compiz but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


so I try the -f


mega@mainpc:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/260kB of archives.
After unpacking 1167kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 138315 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20070917+3v1ubuntu1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070917+3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070917+3v1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mega@mainpc:~$

---

