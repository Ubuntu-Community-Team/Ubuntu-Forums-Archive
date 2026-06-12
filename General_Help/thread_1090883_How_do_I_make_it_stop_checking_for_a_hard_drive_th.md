---
title: "How do I make it stop checking for a hard drive that isn't there?"
date: 2009-03-08
forum: General Help
---

### Post by jeffadams78 on 2009-03-08
I posted this on the apple forums [here]("http://ubuntuforums.org/showthread.php?t=1087627") without any response, but I think it is probably a general enough question that someone here may have a suggestion.

The problem, as near as I can tell, is that on boot, Ubuntu is expecting a second physical hard drive, which I don't have.

Every time it boots there is a delay, then it finally prints this message:

[a number, which I suspect is a timestamp of some sort] hdb: no response (Status code 0xec)

Then it continues booting fine.

I have an emac, which has two ide (is channel the right word?) channels, each of which is a normal IDE channel meaning it has master and slave, so I could have up to four drives theoretically. One channel has my single hard drive on it (which shows up under /dev/hda, it has a pile of partitions as /dev/hda1, /dev/hda2, etc). The other channel has my cdrom drive on it, which shows up as /dev/hdc.

So, it kind of makes sense that hdb doesn't respond... after all, it doesn't exist. How do I make ubuntu quit trying to check it on startup?

The only idea I've had is: I recently replaced the drive, maybe I accidentally set the jumpers wrong on the drive?  Maybe I set it to "Master" instead of "Single"?  Except I know I double-checked it before installing, and plus wouldn't a problem like that show up as an IDE-controller-won't-talk-to-the-drive issue rather than the-os-expects-another-drive?

---

### Post by tommcd on 2009-03-08
Can you post the output of:
```
sudo fdisk -l
```
this will list your hard drives and partitions. Also post the output of:
```
cat /etc/fstab
```
this will list what drives and partitions Ubuntu expects to mount on boot up.

Did you have a flash drive or an external hard drive plugged in to the computer when you installed Ubuntu? If you did, then perhaps it got added to fstab during the install.

---

### Post by dcstar on 2009-03-08
> **jeffadams78 said:**
> 
.......
The only idea I've had is: I recently replaced the drive, maybe I accidentally set the jumpers wrong on the drive?  Maybe I set it to "Master" instead of "Single"?  Except I know I double-checked it before installing, and plus wouldn't a problem like that show up as an IDE-controller-won't-talk-to-the-drive issue rather than the-os-expects-another-drive?

In Ubuntu, hda is the Master device on your Primary IDE channel, hdb is the Slave, hdc is the Master on the Secondary channel etc.

I would speculate that your original install was on a Slave drive on the Master (hdb) and now you replaced the drive with one that is set to Master.

See what happens if you set the new drive to Slave.

---

### Post by jeffadams78 on 2009-03-09
Output from fdisk -l:

```
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Partition_Map_LaCie        63 @ 1         ( 31.5k)  Partition map
/dev/sda2              Apple_Free Extra                 262144 @ 64        (128.0M)  Free space
/dev/sda3               Apple_HFS LaCie              976510928 @ 262208    (465.6G)  HFS
/dev/sda4              Apple_Free Extra                     32 @ 976773136 ( 16.0k)  Free space

Block size=512, Number of Blocks=976773168
DeviceType=0x1, DeviceId=0x1

/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_UNIX_SVR2 swap                10156251 @ 419692608 (  4.8G)  Linux swap
/dev/hda3               Apple_HFS Untitled           419430400 @ 262208    (200.0G)  HFS
/dev/hda4         Apple_Bootstrap boot                    3907 @ 64        (  1.9M)  NewWorld bootblock
/dev/hda5         Apple_UNIX_SVR2 Linux              195293589 @ 429848859 ( 93.1G)  Linux native
/dev/hda6              Apple_Free Extra                 258237 @ 3971      (126.1M)  Free space

Block size=512, Number of Blocks=625142448
DeviceType=0x0, DeviceId=0x0

```

/dev/hda is my internal IDE drive.  /dev/sda is my external firewire drive.  The external drive is always connected, it was connected when I installed and it is also connected now.  I can read it fine (it's hfs+ so it mounts read-only).

contents of /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=d7df9076-0b37-4ece-9e58-030219ee6f14 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda2
UUID=36b5d86e-194f-4e66-b1bd-b98727b4a449 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

dcstar: There was no "original" install, my old drive only had OS X on it.  The replacement is much larger, so I had room to dual-boot and put Ubuntu on it as well.  The new one shouldn't work if I set it to slave; there is no master (I only have one internal hard disk).

I went back and verified, I did indeed set the new one to "single".  It has four options, "Dual/Master", "Dual/Slave", "Single", and "Cable Select".  The manual for the new drive said Apple IDE controllers don't support "Cable Select" and I should use a specific setting.  The old drive (that came with the computer) was jumpered for "CS Enabled" (sounds like cable select to me).

I can try Cable Select if no one has any other suggestions.  Accessing the drive is a royal PITA on an emac though, so that is a last resort.

---

### Post by tommcd on 2009-03-10
Your output of "sudo fdisk -l" shows your 2 hard drives sda (external) and hda (internal). Your fstab only shows 1 drive (hda). I was thinking there might be an extra hdb drive listed in your fstab that you could remove or comment out, but that is not the case. I am not sure why Ubuntu thinks there is a hdb. Don't set the drive to cable select. I don't think that would help. 
Sorry I don't have a better answer. If I can find anything I'll post back.

---

### Post by Yellow Pasque on 2009-03-10
Interesting. I would suggest looking in /boot/grub/device.map and /boot/grub/menu.lst for references to hdb.

---

### Post by jeffadams78 on 2009-03-10
I don't seem to have a "grub" subdir under /boot.
```
root@emac:/boot# ls -al
total 15012
drwxr-xr-x  2 root root    4096 2009-02-24 20:16 .
drwxr-xr-x 20 root root    4096 2009-02-16 21:44 ..
-rw-r--r--  1 root root  434275 2008-09-30 13:37 abi-2.6.25-2-powerpc
-rw-r--r--  1 root root   74306 2008-09-30 13:37 config-2.6.25-2-powerpc
lrwxrwxrwx  1 root root      27 2009-02-16 21:02 initrd.img -> initrd.img-2.6.25-2-powerpc
-rw-r--r--  1 root root 8795955 2009-02-24 20:16 initrd.img-2.6.25-2-powerpc
-rw-r--r--  1 root root  837240 2008-09-30 13:37 System.map-2.6.25-2-powerpc
lrwxrwxrwx  1 root root      24 2009-02-16 21:02 vmlinux -> vmlinux-2.6.25-2-powerpc
-rw-r--r--  1 root root 5167122 2008-09-30 13:37 vmlinux-2.6.25-2-powerpc
root@emac:/boot# 

```

---

### Post by dcstar on 2009-03-10
> **jeffadams78 said:**
> 
........
/dev/hda is my internal IDE drive.  /dev/sda is my external firewire drive.  The external drive is always connected, **it was connected when I installed** and it is also connected now.
........

Then the install process probably identified it as /dev/hdb, and now the actual install identifies it differently.

It is always bad practice to install with any unnecessary stuff attached, the chances of having something out of whack are much greater than installing with just the basic hardware (and then letting the installed system auto-detect later on).

If you do a reinstall without that external drive and everything works ok, then you will have identified a bug in the installation process that needs to be reported.

---

### Post by jeffadams78 on 2009-03-14
That seems possible... but even if it is the case, there should be a significantly simpler solution than reinstalling from scratch.  Somewhere there must be a config file that says "hdb" in it.

---

