---
title: "Intrepid~ cant remove snort!! please help!"
date: 2009-04-15
forum: General Help
---

### Post by KEE on 2009-04-15
this is a thorn! it wont let remove, i cant install apps. it just needs to go. i tried using synaptic package manager and it just i cant either. i always get this error```
The upgrade will continue but the 'snort' package may be in a not working state. Please consider submitting a bug report about it.
``` lol x( need help please and thank you ```
me@me-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libqt4-opengl
  kdebase-runtime-data-common phonon kde-icons-oxygen librasqal0 kdelibs5-data
  libqt4-svg phonon-backend-gstreamer libstreamanalyzer0 libphonon4
  libstreams0 libraptor1 kdebase-runtime-data raptor-utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  snort
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
me@me-desktop:~$ 

```

---

### Post by KEE on 2009-04-15
i tried it again but i can get further then this ```
me@me-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libqt4-opengl
  kdebase-runtime-data-common phonon kde-icons-oxygen librasqal0 kdelibs5-data
  libqt4-svg phonon-backend-gstreamer libstreamanalyzer0 libphonon4
  libstreams0 libraptor1 kdebase-runtime-data raptor-utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  snort
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1065kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140580 files and directories currently installed.)
Removing snort ...
invoke-rc.d: initscript snort, action "stop" failed.
dpkg: error processing snort (--remove):
 subprocess pre-removal script returned error exit status 1
postinst called with unknown argument `abort-remove'
Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by KEE on 2009-04-16
need help please and thank you

---

