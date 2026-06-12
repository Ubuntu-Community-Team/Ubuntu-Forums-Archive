---
title: "Unable to mount, problem with fstab?"
date: 2009-12-27
forum: Desktop Environments
---

### Post by timbalisto on 2009-12-27
I use ubuntu 8.10, I have a media partition called Community Storage that is normally mounted at boot-up and appears on my desktop
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=32cccf65-e896-4e7a-8acc-c46b57b0815d /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda3
UUID=64E5C5544F84B8A7 /media/Community\040Storage ntfs-3g defaults,locale=en_US.UTF-8 0 0

# /dev/sdb5
UUID=244de5fa-d65a-48e6-b367-c41306739ef0 none            swap    sw              0       0
```
It has worked for me for years until now. I didn't shut down Vista properly. When I came back to ubuntu, the media partition didn't mount. I went back to Vista and shut down properly but the problem still persists. When I try to manually mount it, it says ```
You are not privileged to mount the volume 'Community Storage'.
```  and then another pop-up window says ```
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```
The strange thing is that Community storage is listed as sda3 in fstab, but in gparted it's listed as sdb3.
Here is the output of sudo fdisk -l
```
tim@tim-desktop:~$ sudo fdisk -l
[sudo] password for tim: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x084d3596

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14563   116977266    7  HPFS/NTFS
/dev/sda2           14564       21848    58516762+   7  HPFS/NTFS
/dev/sda3           21849       30276    67697910   83  Linux
/dev/sda4           30277       30401     1004062+   5  Extended
/dev/sda5           30277       30401     1004031   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b391b33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1265    10159104    7  HPFS/NTFS
/dev/sdb2            1266        7792    52428127+   7  HPFS/NTFS
/dev/sdb3            7793       38913   249979432+   7  HPFS/NTFS

```
According to this, Community storage is /dev/sdb3
Any help would be appreciated.

---

### Post by apmcd47 on 2009-12-27
I have an external drive on my Linux machine and have noticed that sometimes it is picked up by the OS as sda and sometimes as sdb. The comment in your fstab would have been generated at the time you installed Ubuntu. Because fstab is using the UUID rather than the device name it doesn't matter whether the disk is sda or sdb.

That doesn't help with your problem, but at least you can rest assured that it isn't your problem.

I'd be inclined to first reboot into Vista and run *checkdisk* (is it chkdisk?) on that partition as it is an NTFS partition.

Next time you boot into Ubuntu, if it doesn't mount automatically try mounting as root:

```
sudo mount /media/Community
```

I'm sorry, that is the limit of my expertise in this area. Hopefully someone else will help you if this doesn't.

Andrew

---

### Post by timbalisto on 2009-12-27
I fixed it! First I made the directory
```
sudo mkdir /media/Community\ Storage


```
Then I mounted it using 
```
sudo mount -v /media/Community\ Storage


```
Thanks for the help

---

