---
title: "mount.ntfs-3g keeps working"
date: 2009-02-09
forum: General Help
---

### Post by TheMyself on 2009-02-09
Even though I'm not using the NTFS partition, mount.ntfs-3g is keeping CPU busy. It makes the CPU graph like a comb. Is there any way I can see what it's doing?

---

### Post by darco on 2009-02-12
I seem to be having this issue too...mounted a new hdd, forrmatted to ntfs, rebooted. HDD mounted automatically,  moved files to the new partitions,noticed the cpu at 100%....rebooted, ok but then it started up again....one core pegged at 100%....what gives?

darco

---

### Post by szaka on 2009-02-12
From [http://ntfs-3g.org/support.html#highcpu](http://ntfs-3g.org/support.html#highcpu)

"Some software indeed do intensive file operations sometimes (Beagle, Amarok collectionscanner, updatedb, Spotlight, etc)."

---

### Post by darco on 2009-02-12
> **szaka said:**
> From [http://ntfs-3g.org/support.html#highcpu](http://ntfs-3g.org/support.html#highcpu)

"Some software indeed do intensive file operations sometimes (Beagle, Amarok collectionscanner, updatedb, Spotlight, etc)."

Hey man thanks....I added this line from the link you provided:

VMware is not using "mainMem.useNamedFile=FALSE" in the .vmx file. 

and so far it looks fine...

darco

---

### Post by TheMyself on 2009-02-14
> **szaka said:**
> From [http://ntfs-3g.org/support.html#highcpu](http://ntfs-3g.org/support.html#highcpu)

"Some software indeed do intensive file operations sometimes (Beagle, Amarok collectionscanner, updatedb, Spotlight, etc)."


Well, is there any way to figure out which software is making use of NTFS3G? I don't have any of those ones installed.

---

### Post by szaka on 2009-02-14
> **TheMyself said:**
> Well, is there any way to figure out which software is making use of NTFS3G? I don't have any of those ones installed.
Check out the process list. 

NTFS-3G never uses any CPU time, only on behalf of other software when it is asked to do so to serve them.

---

### Post by adieb on 2009-02-15
Hi,

after booting my mashine, a dual core with 2 HDD (etx3, ext3, ntfs, ntfs) i can see the cpu load is going up, after a  minute after graphical login to gnome.

it is mount.ntfs but only on one of the ntfs partititons. (it is the windows partition, the other ntfs partition just stores files).
(It i not trackerd, I told it not to scan anything)

So i need to kill the pid of that process. After that, in gnome the windows partition is not mounted. when i mount it (by clicking on that hdd symbol in gnome) everything works fine. (no mount-ntfs problems)

What is the reason for that? The problem wasn´t always there. it just came one day.

---

### Post by szaka on 2009-02-15
Mount the NTFS volume from the command line with the 'debug' mount option like
```

sudo mount -t ntfs-3g -o debug DEVICE MOUNTPOINT

where 
DEVICE is an NTFS partition, like /dev/sda1
MOUNTPOINT is an existing directory like /mnt/windows_d

```
then NTFS-3G will show what files are accessed and how, so you can figure out what program is accessing the NTFS volume. Maybe it's Nautilus scanning the directory tree.

---

### Post by adieb on 2009-02-15
good idea! i´ll do that. is it possible put that into fstab? because the "error" comes after booting. if i mount the device after killing mount.ntfs once, there is no special cpu load according to ntfs.

---

### Post by szaka on 2009-02-15
Add the debug option to the others. The log hopefully will go to the 1st terminal.

---

