---
title: "help with file system"
date: 2007-08-06
forum: Dell  Ubuntu Support
---

### Post by jacob01 on 2007-08-06
i was was wondering what some of these partitions are. 
i ran  df -h  to get information about my file system and found a bunch of partitions and was wondering what they are for and what ones are actually usefull


oh yea this is on from one of those dell rigs with ubuntu preinstalled the dell e520n with 250 gig hard drive

jacob@dell:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             226G   20G  195G  10% /
varrun                501M  132K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
procbususb            501M  120K  501M   1% /proc/bus/usb
udev                  501M  120K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm
/dev/sda3             193M   31M  154M  17% /boot
tmpfs                 501M   33M  468M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/scd0             693M  693M     0 100% /media/cdrom0
/dev/sda1              40M  7.7M   32M  20% /media/DellUtility
/dev/sda2             2.0G  691M  1.4G  34% /media/OS

does this look strange to any one else

---

### Post by jacob01 on 2007-08-06
i know that the /dev/sda... are partitions but what are 


the varrun                501M  132K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
procbususb            501M  120K  501M   1% /proc/bus/usb
udev                  501M  120K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm

are they some sort of sub partitions

---

### Post by dougfractal on 2007-08-06
I only know that they are system folders and are temporary.


procbususb   for usb devices
udev  for hotplug
/var/lock   help lock applications so you only get one program with multiple windows e.g. firefox.

---

