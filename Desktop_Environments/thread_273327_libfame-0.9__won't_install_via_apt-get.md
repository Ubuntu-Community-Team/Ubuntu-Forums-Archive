---
title: "libfame-0.9  won't install via apt-get"
date: 2006-10-07
forum: Desktop Environments
---

### Post by preyer on 2006-10-07
Recently I tried to install dvdrip via apt-get. As a dependancy it uses libfame-0.9, but the problems is there is another version of libfame-0.9 alread installed. When trying to install via get the followning output...

```

david@David:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libfame-0.9
The following NEW packages will be installed:
  libfame-0.9
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
37 not fully installed or removed.
Need to get 0B/77.7kB of archives.
After unpacking 319kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 276511 files and directories currently installed.)
Unpacking libfame-0.9 (from .../libfame-0.9_0.9.0-0.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfame-0.9_0.9.0-0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfame-0.9.so.0.0.0', which is also in package libfame0
Errors were encountered while processing:
 /var/cache/apt/archives/libfame-0.9_0.9.0-0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I read somewhere there may be som syncing error with the library but I don't know what this means. 

If someone can tell me how to fix this it would be appreciated.

---

