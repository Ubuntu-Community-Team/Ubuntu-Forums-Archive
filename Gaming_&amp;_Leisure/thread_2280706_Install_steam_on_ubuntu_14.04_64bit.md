---
title: "Install steam on ubuntu 14.04 64bit"
date: 2015-06-01
forum: Gaming &amp; Leisure
---

### Post by alex395 on 2015-06-01
i tried doing the sudo apt-get install steam, but i get this as a result(also new to linux so help would be appreciated)

```
alex@Linux:~$ sudo apt-get install steam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cups : Depends: libc-bin (>= 2.13)
 steam:i386 : Depends: libxinerama1:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
alex@Linux:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  cups cups-bsd cups-client cups-common cups-core-drivers cups-daemon
  cups-server-common libc-bin libcups2 libcupscgi1 libcupsimage2 libcupsmime1
  libcupsppdc1
Suggested packages:
  cups-pdf smbclient xpp
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-core-drivers cups-daemon
  cups-server-common libcups2 libcupscgi1 libcupsimage2 libcupsmime1
  libcupsppdc1
12 upgraded, 1 newly installed, 0 to remove and 259 not upgraded.
Need to get 0 B/2,862 kB of archives.
After this operation, 3,537 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: error: 1 expected program not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by QIII on 2015-06-01
Moved to its own thread.

Posting in someone else's thread that has been marked solved is not likely to get you much help.

---

### Post by MikeCyber on 2015-06-02
Especially as new user I would use synaptic.
It also has a menupoint to fix broken packages etc.

---

