---
title: "Can't mount any USB drive"
date: 2009-03-10
forum: General Help
---

### Post by poolarinn on 2009-03-10
Hey there, you probably get this question all the time, but I've searched through the threads here and followed the information there but it doesn't seem to work.

I have three different USB drives, one iPod nano, one 500gb usb hard drive and one 2gb memory stick. 
I managed to mount the usb stick through terminal, but I can't use it - can't copy anything to it or make new folders(it's newly formatted and totally empty at the moment).

My iPod seems to have a different problem. I can't mount it at all, the information I get is: > DBus error org.freedesktop.dbus.Error.Noreply: Did not recieve a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. and also this 

> Mount is denied because setgid root ntfs-3g is insecure with the external FUSE library. Eiter remove the setuid/setgid bit from the binary or rebuild NTFS-3G with integrated FUSE support and make is setuid root. 

And then there is my large USB drive, it seems to load whenever it wants and sometimes it disconnects for no reason (often when I have been away from the computer for some time, and the screensaver comes on.) 

I have Ubuntu 8.10, IBM thinkpad t43p, and I have also Windows XP installed besides Ubuntu.

-Thanks in advance.

---

### Post by phinullfermata on 2009-03-10
The problem with the first drive mentioned could be that you are using the mount command instead of pmount.  mount usually mounts the drive with root permissions unless you have some settings set to do otherwise.  An easier way of getting permissions to read and write to the drive is to use the pmount command, which mounts the drive as the current user.  Use as:

```
pmount /dev/[usb_device_here] usb
```

which will mount to a directory /media/usb with permission to read and write to the device for the user.

Hope that helps.

---

### Post by poolarinn on 2009-03-11
I get this error when I type what you suggested in terminal:

"device /dev/sdb1 is already handled by /etc/fstab, supplied label is ignored
Mount is denied because setuid and setgid root ntfs-3g is insecure with the
external FUSE library. Either remove the setuid/setgid bit from the binary
or rebuild NTFS-3G with integrated FUSE support and make it setuid root"

---

### Post by poolarinn on 2009-03-12
Can nobody help me with some of those problems? It's really annoying not having the USB drives working...All help is highly appreciated.
BTW, in case you need this information i got from sudo fdisk -l, here it is

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9105    73135408+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            9105        9621     4142880   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            9621       30401   166917681+   f  W95 Ext'd (LBA)
/dev/sda5            9621       24563   120022641+   7  HPFS/NTFS
/dev/sda6           24564       30156    44925741   83  Linux
/dev/sda7           30157       30401     1967931   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 7952 MB, 7952142336 bytes
217 heads, 32 sectors/track, 279 cylinders
Units = cylinders of 6944 * 4096 = 28442624 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         280     7765508    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 32)
Partition 1 has different physical/logical endings:
     phys=(120, 216, 32) logical=(279, 126, 32)

Disk /dev/sdc: 2003 MB, 2003828736 bytes
16 heads, 32 sectors/track, 7644 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xcf7a032e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          16        7644     1952832    b  W95 FAT32


Dev sdc is my small USB memory stick, and the dev sdb is my ipod.

---

### Post by Hobgoblin on 2009-03-12
Can you post the contents of your /etc/fstab ?

---

### Post by tacosaviour on 2009-03-12
> **phinullfermata said:**
> The problem with the first drive mentioned could be that you are using the mount command instead of pmount.  mount usually mounts the drive with root permissions unless you have some settings set to do otherwise.  An easier way of getting permissions to read and write to the drive is to use the pmount command, which mounts the drive as the current user.  Use as:

```
pmount /dev/[usb_device_here] usb
```

which will mount to a directory /media/usb with permission to read and write to the device for the user.

Hope that helps.

I was having the same issue, and your solution worked for me!

Thank you!

---

### Post by poolarinn on 2009-03-13
Here is the info from /etc/fstab:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=07af5fdd-8ffc-4049-b0a1-a5b70897b1ed / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=2c7b2fe5-d3fd-422d-87a9-ff2f22a06322 none swap sw 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_DK.UTF-8 0 0
/dev/sda5 /media/sda5 ntfs-3g defaults,locale=en_DK.UTF-8 0 0
/dev/sda6 /media/sda6 ext3 defaults 0 0
/dev/sda7 /media/sda7 swap defaults 0 0
/dev/sdc1 /media/iPod ntfs-3g users,user,owner 0 0
/dev/sdb1 /media/usb ntfs-3g users,user,owner 0 0

```

---

### Post by poolarinn on 2009-03-13
I think I have fixed this problem, I went to Storage Device Manager, found the devices there, and did Remove, which removed my previous settings(which seems like I had ****** up). Then I mounted the devices again, and it worked ;)

---

