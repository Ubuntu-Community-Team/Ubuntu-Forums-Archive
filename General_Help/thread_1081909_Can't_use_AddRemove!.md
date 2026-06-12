---
title: "Can't use Add/Remove!"
date: 2009-02-27
forum: General Help
---

### Post by msohn88 on 2009-02-27
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Er...

---

### Post by adult swim on 2009-02-27
what does ```
ls -l /etc/apt/sources.list

sudo apt-get install -f
``` return when you enter it into a terminal?

---

### Post by msohn88 on 2009-02-27
min@min-laptop:~$ ls -l /etc/apt/sources.list
-rw-r--r-- 1 root root 2918 2009-02-26 22:55 /etc/apt/sources.list
min@min-laptop:~$ 
min@min-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libqt4-opengl libxine1-x
  kdebase-runtime-data-common libqt4-test libxine1-misc-plugins libxcb-xv0
  phonon libqt4-core libfftw3-3 kde-icons-oxygen libxine1-bin librasqal0
  libakonadiprivate1 kdelibs5-data libxcb-shape0 libqt4-svg
  phonon-backend-gstreamer libstreamanalyzer0 libphonon4 libxvmc1 libstreams0
  libraptor1 libxcb-shm0 kdebase-runtime-data raptor-utils kdepimlibs-data
  libofa0 libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 219 not upgraded.
min@min-laptop:~$

Which means, it's working now. Thanks!

---

### Post by zvacet on 2009-02-27
```
sudo apt-get update && sudo apt-get upgrade
```

Do this for upgrading 219 packages whitch are not upgraded.

---

### Post by msohn88 on 2009-02-27
Is this the update that is required after you installed first version of 8.10?

I think I installed it by cilcking the "down" button on the top right corner of it.

Or is this another installation?

Thanks for in advance.

---

