---
title: "HDD mounting in the wrong place"
date: 2009-01-27
forum: General Help
---

### Post by OdSquad64 on 2009-01-27
I have a hdd whose label is 500GB that is supposed to mount in /media/500GB However it creates a folder called 500GB_ in media and mounts there instead.  I'm not sure how to fix this, but I can't image it is too difficult.

Here is my fstab:

proc /proc proc defaults 0 0
# Entry for /dev/sdb2 :
UUID=b19ae782-2bbc-436a-adb2-4b379871640e / ext3 defaults,errors=remount-ro,relatime 0 1
# Entry for /dev/sdb1 :
UUID=ACA429A0A4296DD0 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sdb3 :
UUID=175e95a0-9dd3-4ae1-b8fb-d2b0fc03ee8a none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
#Entry for /dev/sdc1
UUID=42fa0ebb-4245-41fa-94a2-800f703a5938 /media/750GB xfs defaults 0 0
#Entry for /dev/sdd1
UUID=f4dda7c9-7170-4e86-9c50-51611d37b004 /media/500GB xfs defaults 0 0
#Entry for /dev/sda1
UUID=29635c8d-d097-4bea-8e32-30b6e503e641 /media/1TB xfs defaults 0 0

Any help is greatly appreciated.

---

### Post by amac777 on 2009-01-27
If it's a USB harddrive with a label (using e2label etc), it should mount automatically in a directory with the same name as the label when you plug it in. You don't need to pre-create the mount point or have the hard drive listed in your fstab. 

Try:

1. unmount 500GB, 
2. unplug the hard drive
3. remove the empty mount point directory /media/500GB, 
4. comment out the fstab line for /media/500GB
5. then plug in the hard drive and see if it mounts in the right spot

---

### Post by OdSquad64 on 2009-01-27
wow it worked, thanks a lot, before i always needed an existing folder for the mount point, i guess thats not the case anymore.

---

