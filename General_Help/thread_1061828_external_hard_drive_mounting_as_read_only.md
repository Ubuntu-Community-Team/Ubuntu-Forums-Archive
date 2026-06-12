---
title: "external hard drive mounting as read only"
date: 2009-02-06
forum: General Help
---

### Post by LordIshamael on 2009-02-06
hey im using kubuntu 8.10
i have an external hard drive 320 gb, whenever i mount it it mounts as read only, so i cant copy anything to it, rename files or delete anything
i tried changing permission - chmod - and ownership - chown - but it says its a read only filesystem, and cant be changed
ive tried these commands with sudo as well, still didnt work
it works fine under vista though
its a fat 32 filesystem btw, and ive had it for some months and never had this problem before the past couple of weeks
i got the uuid of the filesystem, added it to /etc/fstab (it wasnt in it before) with the mount point given and everything else blank
now it wont mount unless i give the command as root
also, if i remove and plug it back in, the device name changes ie from sdb1 to sdc1, then to sdd1 etc
then later it reverts to sdb1
once ive mounted it as root, then i can access files, but its back to being read only, even if i mounted with the option -o rw

any idea whats going on and how to fix it?

---

### Post by vanadium on 2009-02-06
Remove the drive from /etc/fstab. An external drive does not belong there unless you want to mount it manually from the command line. Restart the system.

Have the file system of the drive checked. You can do that in Ubuntu with the dosfsck utility. First unmount the drive, then run "dosfsck -a <device name>" where <device name> is the device name of the partition, which looks like for example "/dev/sdb1". You can see the device names of all your partitions with the "sudo blkid" command.

The -a switch means "automatically repair file system". If you run dosfsck without option, a diagnosis, but no repair, will be performed.

Then disconnect and connect the drive again.

---

### Post by LordIshamael on 2009-02-06
yep
that worked! thanks a lot! this really saves me a lot of headache

---

### Post by LordIshamael on 2009-02-06
id thank you, and mark this thread solved, but apparently thats disabled for now...

---

