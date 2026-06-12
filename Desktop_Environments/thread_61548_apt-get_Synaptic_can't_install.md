---
title: "apt-get /Synaptic can't install?"
date: 2005-09-01
forum: Desktop Environments
---

### Post by spedsta on 2005-09-01
I tried to install two seperate packages(3d chess and Pan), not releated in any way using both synaptic and apt-get install.  here are the printouts of both:

(Reading database ... dpkg: error processing /var/cache/apt/archives/libgnet2.0-0_2.0.4-1_i386.deb (--unpack):
 unable to open files list file for package `libxmuu1': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libgnet2.0-0_2.0.4-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


(Reading database ... dpkg: error processing /var/cache/apt/archives/3dchess_0.8.1-11_i386.deb (--unpack):
 unable to open files list file for package `libxmuu1': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/3dchess_0.8.1-11_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

please help  :|

---

### Post by Omning on 2005-11-13
I'm actually running into the same problem, on all apt-get's/synaptic/add application
Here's an output of what happens when I try apt-get -f install

```
sudo apt-get -f install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblame0
The following NEW packages will be installed:
  gstreamer0.8-lame liblame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 187kB of archives.
After unpacking 504kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com breezy/multiverse liblame0 3.96.1-1 [151kB]
Get:2 http://us.archive.ubuntu.com breezy/multiverse gstreamer0.8-lame 0.8.11-0u buntu1 [35.3kB]
Fetched 187kB in 1s (133kB/s)

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3. 96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
tdear@serenity:/var/cache/apt/archives$ sudo apt-get -f install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblame0
The following NEW packages will be installed:
  gstreamer0.8-lame liblame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/187kB of archives.
After unpacking 504kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have no idea what's going on.

---

### Post by arnieboy on 2005-11-14
[QUOTE=Omning]I'm actually running into the same problem, on all apt-get's/synaptic/add application
Here's an output of what happens when I try apt-get -f install

```
sudo apt-get -f install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblame0
The following NEW packages will be installed:
  gstreamer0.8-lame liblame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 187kB of archives.
After unpacking 504kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com breezy/multiverse liblame0 3.96.1-1 [151kB]
Get:2 http://us.archive.ubuntu.com breezy/multiverse gstreamer0.8-lame 0.8.11-0u buntu1 [35.3kB]
Fetched 187kB in 1s (133kB/s)

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3. 96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
tdear@serenity:/var/cache/apt/archives$ sudo apt-get -f install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblame0
The following NEW packages will be installed:
  gstreamer0.8-lame liblame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/187kB of archives.
After unpacking 504kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb (--unpack):
 unable to open files list file for package `libbonoboui2-0': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/liblame0_3.96.1-1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have no idea what's going on.[/QUOTE]
please paste the contents of */etc/apt/sources.list*

---

