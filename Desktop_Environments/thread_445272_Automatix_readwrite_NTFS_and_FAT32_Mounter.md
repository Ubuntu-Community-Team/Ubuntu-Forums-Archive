---
title: "Automatix read/write NTFS and FAT32 Mounter"
date: 2007-05-15
forum: Desktop Environments
---

### Post by srtraveler on 2007-05-15
I am running V.7 and wonder if this is a good thing to install. My main concern is will it cause any problems when it automatically mounts all local FAT32 and NTFS partitions and makes them writable. I have 2 programs that I miss or would like to be able to use: Itunes and Nutribase, the latter a diet and exercise log--but much more than that.

---

### Post by Saphira on 2007-05-16
Automatix is unnessecary for the application of NTFS/FAT accessing. Automatix is well-known for breaking systems and you'll find that you really don't need it. It makes upgrading your system later difficult. 

Try following the links below

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[https://help.ubuntu.com/community/MountNtfsOnBoot](https://help.ubuntu.com/community/MountNtfsOnBoot)

[https://help.ubuntu.com/community/RestrictedFormats/iTunesMusicStore](https://help.ubuntu.com/community/RestrictedFormats/iTunesMusicStore)

[http://packages.ubuntu.com/feisty/misc/nut-nutrition](http://packages.ubuntu.com/feisty/misc/nut-nutrition)

sudo apt-get install nut-nutrition

Hope this helps.

---

### Post by kelvin spratt on 2007-05-16
i use automatix for ntfs read and write and it does a better job than the official version, and is very stable. I wish people would not slag things of just a warning to use caution is sufficient as Microsoft has done for years Automatix brings things out before the repro as do the developers, they also bring out bug fixes as in the exe world that cure things like the sound problem in devede and fiesty yes a patch, embrace progress don't put it down. Other wise in 10 years you will be where you are now.

---

### Post by taurus on 2007-05-16
> **kelvin spratt said:**
> i use automatix for ntfs read and write and it does a better job than the official version, and is very stable.

Am I missing something here?  They both install ntfs-3g and as far as I know, ntfs-3g from the repos and the one from Automatix are the same.  Therefore, you can install ntfs-3g & ntfs-config through synaptic/apt-get/aptitude so what's the point of adding extra stuff to your /etc/apt/sources.list when you don't really need it.

---

