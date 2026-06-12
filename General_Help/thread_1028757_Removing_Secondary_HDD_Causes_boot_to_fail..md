---
title: "Removing Secondary HDD Causes boot to fail."
date: 2009-01-02
forum: General Help
---

### Post by RobbieCrash on 2009-01-02
I'm trying to move a hard drive from my Ubuntu box to a different computer, but every time I remove it, I can only boot into BusyBox. 

I know that the hdd that I'm moving off isn't the hdd that Ubuntu is installed on, and it's not even mounted. If I attach a CDROM to the same IDE channel that the HDD was on, the system boots fine. So I'm pretty sure it's a problem with GRUB and where it's pointing to boot from. But everything looks right to me there. 

Anyone have any idea what I need to change? 

/etc/fstab and the grub files are here: [http://pastebin.ca/1298632](http://pastebin.ca/1298632)

---

### Post by dcstar on 2009-01-02
> **RobbieCrash said:**
> I'm trying to move a hard drive from my Ubuntu box to a different computer, but every time I remove it, I can only boot into BusyBox. 
.........

The install process customises many things to the particular hardware that a system has, moving a disk to a system with different hardware is unlikely to work.

Install Ubuntu in the normal way on the new hardware, and then copy any data you need from the old disk.

---

### Post by RobbieCrash on 2009-01-02
It is a secondary hard drive, not the primary hdd. Ubuntu is not installed on the drive I am trying to move. Which was explained in my original post, in the part that you ellipsesed out. But perhaps I was unclear in my original post:

System 1:
Ubuntu box, with 4 IDE HDDs, 4 SATA HDDs, one IDE CDROM.
3 IDE HDD are in use, all 4 SATA drives are in use, the CDROM drive is not in use routinely.

System 2:
Nothing yet, will have the 1 IDE drive not in use on system 1, and the CDROM drive.

System 1 boots off of IDE HDD 1, which shares an IDE channel with IDE HDD 0

I want to move IDE HDD 0 and the IDE CDROM from system 1 to System 2, but every time I remove that drive the box will only boot to busybox. Jumper settings on the IDE drive have been changed to reflect the drive now being the only drive on the channel.

Reattaching the drive lets the system boot fine, even though it is a blank unformatted, unpartitioned, unconfigured and unmounted drive. 

If I then attach the CDROM to the same IDE channel that HDD 0 was originally on, the system boots fine, everything works.

I believe this to be a problem caused by some enumeration of the devices on that particular IDE channel, and the way that GRUB is looking for what disk/partition to boot from. But since everything in GRUB is set up to go by UUID, I don't see how this is possible. The information in menu.lst matches up to the information in my fstab, so I'm not sure what needs to be reconfigured in order to get this booting without the additional IDE drive.

---

### Post by Snow986 on 2009-01-02
Don't know if this is correct but kinda sounds to me like when it checks the drive channels during boot up and hdd 0 is empty it is causing an error.  I would say change hdd 1 over to hdd 0 and have it boot from hdd 0.  Then move each other hdd down one and i bet everything will boot fine.  You could probably get away with moving one of your hdd 2 or 3 down to 0 and trying to boot.

---

### Post by dcstar on 2009-01-02
> **RobbieCrash said:**
> It is a secondary hard drive, not the primary hdd. Ubuntu is not installed on the drive I am trying to move. Which was explained in my original post, in the part that you ellipsesed out. But perhaps I was unclear in my original post:
........
I believe this to be a problem caused by some enumeration of the devices on that particular IDE channel, and the way that GRUB is looking for what disk/partition to boot from. But since everything in GRUB is set up to go by UUID, I don't see how this is possible. The information in menu.lst matches up to the information in my fstab, so I'm not sure what needs to be reconfigured in order to get this booting without the additional IDE drive.

Yes, it wasn't 100% clear to me but my comments still apply.

Grub is loading your system, it is the existing configuration that expects the hardware you are removing to actually be there.

The existing configuration (*not* Grub) probably has various sda/hda designations that change because of the hardware you remove, so you experience the problems you have.

You will need to go through your system with the proverbial "fine tooth comb" and try and identify where these are, and then try and figure out what to do with them.

---

### Post by dcstar on 2009-01-02
> **RobbieCrash said:**
> It is a secondary hard drive, not the primary hdd. Ubuntu is not installed on the drive I am trying to move. Which was explained in my original post, in the part that you ellipsesed out. But perhaps I was unclear in my original post:

System 1:
Ubuntu box, with 4 IDE HDDs, 4 SATA HDDs, one IDE CDROM.
......

Since most systems only allow a total of 4 IDE devices, how do you have 5?

---

### Post by RobbieCrash on 2009-01-03
> **Snow986 said:**
> Don't know if this is correct but kinda sounds to me like when it checks the drive channels during boot up and hdd 0 is empty it is causing an error.  I would say change hdd 1 over to hdd 0 and have it boot from hdd 0.  Then move each other hdd down one and i bet everything will boot fine.  You could probably get away with moving one of your hdd 2 or 3 down to 0 and trying to boot.

The drives on IDE 2 and 3 are part of a FakeRAID array. Which I know, I know, is not an ideal solution to a tricky problem, but it is none-the-less the solution I have at hand. 

So I can't move either of them without having to break, and rebuild the array. Which is easy enough on a real RAID controller, but hasn't ever worked out properly for me on a fake one.

> **dcstar said:**
> Yes, it wasn't 100% clear to me but my comments still apply.

Grub is loading your system, it is the existing configuration that expects the hardware you are removing to actually be there.

The existing configuration (*not* Grub) probably has various sda/hda designations that change because of the hardware you remove, so you experience the problems you have.

You will need to go through your system with the proverbial "fine tooth comb" and try and identify where these are, and then try and figure out what to do with them.

So does the system really care after everything is loaded? Because even with a CD ROM drive in place of the second IDE HDD, the system boots and runs fine, and can access the CD ROM drive.

According to /etc/fstab, the CD ROM drive is loaded as scd0, not as hd* or sd*. So if it really is the case that it's my system that needs there to be a matching configuration in its own hd*/sd* world, why does it not care if there's a CD ROM in place of an HDD?

> **dcstar said:**
> Since most systems only allow a total of 4 IDE devices, how do you have 5?

On this build I had a PCI IDE card, However, two of my other computers have motherboards which support up to 8 devices.

---

### Post by fjgaude on 2009-01-03
What does **fdisk -l** show for the mounted devices?

Please show your **fstab** file. If you are not using UUIDs to mount your issue could be drive names changing.

---

### Post by RobbieCrash on 2009-01-03
> **fjgaude said:**
> What does **fdisk -l** show for the mounted devices?

Please show your **fstab** file. If you are not using UUIDs to mount your issue could be drive names changing.

```
robbie@thoth:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc
Cannot open /dev/sdd
Cannot open /dev/sde
Cannot open /dev/sdf
Cannot open /dev/sdg
Cannot open /dev/sdh
robbie@thoth:~$ sudo !!
sudo fdisk -l
[sudo] password for robbie:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a64e0b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033601   83  Linux

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a64e0b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36481   293033601   83  Linux

Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001ddbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       24321   195358401   83  Linux

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          64      514048+  83  Linux
/dev/sdf2              65        1369    10482412+  83  Linux
/dev/sdf3            1370        3980    20972857+  83  Linux
/dev/sdf4            3981       14593    85248922+   5  Extended
/dev/sdf5            3981        9202    41945683+  83  Linux
/dev/sdf6            9203       11813    20972826   83  Linux
/dev/sdf7           11814       13771    15727603+  83  Linux
/dev/sdf8           13772       14593     6602683+  82  Linux swap / Solaris

Disk /dev/sdg: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001ddbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       24321   195358401   83  Linux

Disk /dev/sdh: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       18891   151741926   83  Linux
/dev/sdh2           18892       19457     4546395    5  Extended
/dev/sdh5           18892       19457     4546363+  82  Linux swap / Solaris
robbie@thoth:~$
```

fstab is using UUID's for the system partitions, but /dev/mapper/blah blah for the FakeRAID arrays, and my two USB backup drives:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdh2
UUID=d5611b7c-a45c-4a8e-9b59-e7b0fa84007f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdh1
UUID=0f5af291-b15a-4c82-8929-121a02d6b131 /boot           ext3    relatime        0       2
# /dev/sdh6
UUID=2e0e9d5a-c9a3-4d1e-806a-5f45d08a0582 /home           xfs     relatime        0       2
# /dev/sdh7
UUID=af645c49-61ac-48aa-8c24-5895f8869c4d /tmp            xfs     relatime        0       2
# /dev/sdh3
UUID=1e583c73-97b1-459a-a237-ef4774f0bf2e /usr            ext3    relatime        0       2
# /dev/sdh5
UUID=71057547-ce1d-480b-b5dd-9893a43df964 /var            xfs     relatime        0       2
# /dev/sdh8
UUID=a3157863-1fb3-42fe-85d5-0963ed7f7734 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


# RAID Arrays:
/dev/mapper/nvidia_ddefbebi1		/movies		xfs	relatime	0	0
/dev/mapper/nvidia_idifdahh1		/music		xfs	relatime	0	0
/dev/mapper/nvidia_agbfbeih1		/documents	xfs	relatime	0	0

# Backup drives:
/dev/sdi1 				/backup		reiserfs	rw,nosuid,nodev,uhelper=hal	0	0
/dev/sdj1 				/backup		reiserfs	rw,nosuid,nodev,uhelper=hal	0	0
```

---

### Post by fjgaude on 2009-01-03
I can't see anything wrong with what you show. I guess the sdh and the sdf have switched without you knowing it? Can't say from which you are really booting from. <smile>

What drive name is it that you are wanting to take out?

---

### Post by dcstar on 2009-01-04
> **RobbieCrash said:**
> 
.........
So does the system really care after everything is loaded? Because even with a CD ROM drive in place of the second IDE HDD, the system boots and runs fine, and can access the CD ROM drive.

According to /etc/fstab, the CD ROM drive is loaded as scd0, not as hd* or sd*. So if it really is the case that it's my system that needs there to be a matching configuration in its own hd*/sd* world, why does it not care if there's a CD ROM in place of an HDD?
.........

Something is relying on an IDE device to exist (no matter what it actually is), you may need to carefully examine the syslog to see what is probing the IDE devices on boot-up.

---

