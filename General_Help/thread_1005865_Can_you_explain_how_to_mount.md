---
title: "Can you explain how to mount"
date: 2008-12-08
forum: General Help
---

### Post by rusty_jones on 2008-12-08
```
Disk /dev/sdc: 1053 MB, 1053556736 bytes
255 heads, 63 sectors/track, 128 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73696420

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         128     1028128+   5  Extended

```

This is what i get when i do: sudo fdisk -l

I know there is a way to mount a drive with this info but I don't understand it. Can someone explain this to me. I'm also new to ubuntu.

---

### Post by Sjeti on 2008-12-08
You first want to create the directory you want to mount it to, normally:
```

sudo mkdir /media/whatever

```
Then you need to actually mount it:
```

sudo mount /dev/sdc1 /media/whatever

```
The first target is what you are mounting, the second is where you are mounting it to.  If you are mounting something like an ISO though, you will want to add the -o loop modifier after mount.

Also, if you need to unmount the volume it would be:
```

sudo umount /media/whatever

```
All you need to know is the mount point.

---

### Post by bodhi.zazen on 2008-12-08
You do not mount extended partitions. You first need to make a logical partition within the extended partition.

You then can mount with

```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```

options (such as permissions) are dependent on the file system.


See also :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by rusty_jones on 2008-12-09
When I try these commands it ask for a file type. I'm trying to mount aa fat32 thumb drive.

Rusty

---

### Post by stefangr1 on 2008-12-09
> **rusty_jones said:**
> When I try these commands it ask for a file type. I'm trying to mount aa fat32 thumb drive.

Rusty

If a thum drive can't be automatically mounted when you insert it, there's likely to be something wrong, and you will most likely not be able to mount it manually.

---

