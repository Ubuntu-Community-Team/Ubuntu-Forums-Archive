---
title: "Error installing Nethack"
date: 2009-03-13
forum: General Help
---

### Post by Mrbill86 on 2009-03-13
I've been watching some friends playing Nethack so I decided to give it a try.  So here's what happens whenever I try and install it:

```
thomas@Laptop:~$ sudo apt-get install nethack-console
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libqt4-opengl libxine1-x librdf0
  kdebase-runtime-data-common libqt4-sql-mysql libqt4-dbus
  libxine1-misc-plugins kdelibs5 libxcb-xv0 phonon libqt4-qt3support
  libxine1-bin librasqal0 libsoprano4 redland-utils kdelibs5-data libqtcore4
  libxcb-shape0 libqt4-sql libqt4-svg phonon-backend-gstreamer
  libstreamanalyzer0 libphonon4 libqt4-xml libqt4-network libqt4-designer
  kdelibs-bin libqtgui4 libpq5 libstreams0 libraptor1 libmodplug0c2
  libqt4-script libxcb-shm0 soprano-daemon kdebase-runtime-data raptor-utils
  qt4-qtconfig libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nethack-common
The following NEW packages will be installed:
  nethack-common nethack-console
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 855kB/1319kB of archives.
After this operation, 3293kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid/universe nethack-console 3.4.3-10.5ubuntu1 [855kB]
Fetched 855kB in 9s (89.3kB/s)                                                 
Preconfiguring packages ...
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by LegendofTom on 2009-03-13
try running 

```
sudo apt-get -f install
```
then try:
```
sudo dpkg --configure -a
```
or maybe you just need to:
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```

---

