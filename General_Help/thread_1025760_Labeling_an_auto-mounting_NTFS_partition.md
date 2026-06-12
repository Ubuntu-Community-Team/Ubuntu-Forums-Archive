---
title: "Labeling an auto-mounting NTFS partition"
date: 2008-12-30
forum: General Help
---

### Post by sexyclient on 2008-12-30
Howdy, I'm trying to get an NTFS partition to automatically mount on startup (at /media/data) and give it the label "data" so that it would appear in nautilus as "data" instead of "<disksize> media".

I edited fstab to get the ntfs partition (/dev/sde6) to auto-mount and it now looks like this: ```
proc                                       /proc          proc         defaults                    0  0  
# Entry for /dev/sde4 :
UUID=87e4e51f-ffa2-4db2-a9e2-e7abe8753ef5  /              ext3         relatime,errors=remount-ro  0  1  
# Entry for /dev/sde5 :
UUID=6b1355a8-d4f3-4233-b8d7-96d17508f4c8  none           swap         sw                          0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd0                                  /media/cdrom1  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sde6                                  /media/data    ntfs         defaults                    0  0  
```
That's done and working - but I can't un-mount it in nautilus.  Even worse, when I try to use ntfslabel on it, I keep getting a "permission denied" error - even if I use sudo ntfslabel.  I tried unmounting then using ntfslabel, then I tried removing the fstab entry, restarting so it's never mounted at all, then using ntfslabel - but I still get permission denied.  I've fooled around with the options in fstab but still haven't gotten anything to work.  I'm lost :(

---

### Post by mc4man on 2008-12-30
You may wish to read carefully here concerning ntfs internal drives.
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

As far as changing label ntfslabel works well

EX. run this to ck. current label (volume should not be mounted

> doug@doug-desktop:~$ sudo ntfslabel /dev/sda2
[sudo] password for doug: 
PROGS

To change 
> doug@doug-desktop:~$ sudo ntfslabel /dev/sda2 PROGS1

---

### Post by sexyclient on 2009-01-02
Thanks, but I tried that.  I just went into windows to change it.

---

