---
title: "Hello and ? on minimum requirements"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Gasman on 2005-11-17
Hello all.  I first heard of Ubuntu yesterday, downloaded the Live cd of 5.10 to demo and am attempting my first install this evening.

I have an old desktop I would like to install on, but don't know if I'm selecting the right parameters on the setup.

The hard drive is only 3.5 GB.  The partitioner set it up this way:

IDE1 master (hda) - 3.5 GB FUJITSU MPA3035ATU
     #1 primary  255.0 MB  ext3  /boot
     #5 logical       3.2 GB  lvm

LVM VG Ubuntu, LV root - 3.1 GB Unknown
     #1  3.1 GB  ext3
LVM VG Ubuntu, LV swap_1 - 172.0 MB  Unknown
     #1  172.0 MB  swap  swap

I ran the install once and got the error:

* * * * * * *
[!!]Install the base system
Unable to install the selected kernel into the target system

Kernal package:  'linux-386'
Check  /target/var/log/bootstrap.log for the details
* * * * * * *

I'm not sure how to get to the bootstrap.log at this point and don't know if this small old disk would work anyway.

Any ideas?
Gasman

---

### Post by Gasman on 2005-11-17
I'm happy to report that I re-ran the partitioner with the same configuration and it continued with the installation this time.  The system has rebooted and is installing the packages now.

I did run across this info in the wiki:  Be aware that "Breezy Badger" requires about 1.8 Gb to install and operate, and any less than a 4 Gb root (/) partition with a 256 Mb swap partition can make the install process stop abruptly."

Looks like it's going to complete the install :cool:

Gasman

---

### Post by PDXlewis on 2005-11-19
So, how is it running? I am looking into using some older systems for a school lab and wonder if it is worth it.

was wondering about min requirements myself.

---

### Post by Gasman on 2005-11-26
Hi PDXlewis,

It seems to be running fine.  I think a bit more RAM would be nice on this box, but other than that, I'm pretty satisfied.  I also installed on a PII 400 MHZ and find it is definitely quicker on that box.  

One issue I have on both of these Compaq Deskpros is getting the ESS 1869 sound card running, but it hasn't been a priority.

Cheers
Gasman

---

