---
title: "External eSATA drive not auto-mounted when plugged in"
date: 2009-02-20
forum: General Help
---

### Post by UranUtan on 2009-02-20
Hi,

Using Ubuntu 8.10 x32, 1 single 160 GB IDE hard drive. I have connected an eSATA bracket to an internal SATA connector on my motherboard. Then I connect an external drive which has two modes of connection USB and eSATA.

When connected by USB, the drive is auto-mounted and appears on the desktop. Then I unmounted, powered off the external drive, replaced the USB cable by a SATA cable. Then power on the external drive. The new drive doesn't appear on the desktop. What is the reason and how to fix it? 

Here are fdisk and blkid info as I saw people use to ask these info for similar issue.
```

/dev/sda1: UUID="380572cf-dea6-4b32-896f-0c0c0525aac5" TYPE="ext3" 
/dev/sda5: UUID="d94dda73-78b9-4839-90e5-344833bcb73e" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="50fc9ae6-81e6-4628-9196-4d4d47870917" 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdb05cbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       19457   146520832+   5  Extended
/dev/sda5            1217       18849   141637041   83  Linux
/dev/sda6           18850       19457     4883728+  82  Linux swap / Solaris
```

May be my eSATA bracket is not working properly. Is there any way I can diagnose the presence of the external drive via eSATA ?


Thanks in advance for any help.

---

### Post by Yellow Pasque on 2009-02-20
> May be my eSATA bracket is not working properly. Is there any way I can diagnose the presence of the external drive via eSATA ?

Hopefully, lshw will show it. You may need to build a kernel module/driver for it.
```
sudo lshw
```

---

### Post by UranUtan on 2009-02-20
Hi,

Thanks for your quick answer. **lshw** is really a cool instruction. I always wanted to know about the inventory of hardware, now I know.

The output doesn't hint anything about the external eSATA drive. How can I build a kernel module/driver?

---

### Post by Yellow Pasque on 2009-02-20
Actually, I'm not sure if an eSATA bracket would even need a driver or show up in lshw.
My next suggestion would be to connect the drive via eSATA and check if the drive shows up in the BIOS.

---

### Post by UranUtan on 2009-02-21
Seem like the external drive connected via the eSATA port is not hot plugged on this computer (or may be Ubuntu doesn't recognized it as hot plug).

After power off / on. I see the external drive (connected to eSATA) listed in the BIOS screen. Then Ubuntu starts as usual. Here is the output of **sudo fdisk -l**
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdb05cbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       19457   146520832+   5  Extended
/dev/sda5            1217       18849   141637041   83  Linux
/dev/sda6           18850       19457     4883728+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbc55182

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

sudo blkid
/dev/sda1: UUID="380572cf-dea6-4b32-896f-0c0c0525aac5" TYPE="ext3" 
/dev/sda5: UUID="d94dda73-78b9-4839-90e5-344833bcb73e" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="50fc9ae6-81e6-4628-9196-4d4d47870917" 
/dev/sdb1: UUID="A8789057789025DA" LABEL="NexStar500G" TYPE="ntfs"
```

I open Nautilus and clicked on the drive. A popup screen says "system policy prevents from mounting an internal drive" and asks for password. When pwd OK, I can see the content of the drive.

[COLOR="Red"]**Q1.**[/COLOR] What is the mount syntax that would allow me to use this external drive (listed as /dev/sdb1) immediately?

[COLOR="Red"]**Q2.**[/COLOR] What should I do to mount this drive permanently so it could be used by all users.

Thanks in advance for any help.

---

### Post by UranUtan on 2009-02-21
For Q1, I got the answer here [http://ubuntuforums.org/showthread.php?t=1026414](http://ubuntuforums.org/showthread.php?t=1026414) Here is what I did can you please suggest/comment if there is a better way?
```
sudo mkdir /media/satadrive1
sudo mount -t ntfs-3g /dev/sdb1 /media/satadrive1

```

For Q2 which also covers Q1 [http://ubuntuforums.org/showthread.php?t=1073859](http://ubuntuforums.org/showthread.php?t=1073859)
I must edit fstab. I am not sure what to put there, can you please help me for the syntax?

The drive is NTFS and all users must be able to read/write on this drive.

Thanks

---

### Post by Yellow Pasque on 2009-02-21
Do you have multiple users on your system?

If you just have one user, you would use this in your fstab:
```
UUID=A8789057789025DA  /media/satadrive1  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
```

---

### Post by Yellow Pasque on 2009-02-21
Also, for hot-swapping to work, you may need to set your SATA mode to AHCI in the BIOS.

---

### Post by UranUtan on 2009-02-21
> **Temüjin said:**
> Do you have multiple users on your system?

If you just have one user, you would use this in your fstab:
```
UUID=A8789057789025DA  /media/satadrive1  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0
```

Thanks very much for your help. I have 3 users. I would like ALL users having Read/Write access on this eSATA external drive.

Can it be done by tweaking some options in the fstab line you suggested above?

---

### Post by Yellow Pasque on 2009-02-21
> Can it be done by tweaking some options in the fstab line you suggested above?
Yes, but first you should see if it's working with hotplugging, because that would make life easier.
> I have 3 users
Is your system a server of some kind or are these just 3 different profiles? Also, how are you using this drive? Backup?

---

### Post by UranUtan on 2009-02-22
> **Temüjin said:**
> Yes, but first you should see if it's working with hotplugging, because that would make life easier.
The computer is an IBM ThinkCentre Tower A50. It is almost 5 years old. The BIOS setup screen doesn't list anything about SATA to set the mode to AHCI. There are two settings 1) Serail ATA: Disabled / Enabled. 2)Native Mode Operation: Automatic / Serial ATA. Current setting is Enabled, Automatic.

> **Temüjin said:**
> Is your system a server of some kind or are these just 3 different profiles? Also, how are you using this drive? Backup?This is a desktop machine. Each user has different profiles (wallpaper, bookmarks in Firefox, login in Pidgin, etc. Also, the account used by my wife has less privileges. For example: she will never install driver or do anything with system settings.

> **Temüjin said:**
> Also, how are you using this drive? Backup?
This drive will be used as an external hard drive. Any user can read / write on it. For example: I download, drivers, ISO, etc. I store on this drive. My wife downloads some media files, she stores them on this drive in her folder. My daughter offloads the photos of her camera and stores them in a folder on this drive. So we use this drive like a normal hard drive: a "container" where we store and retrieve files. We may also rename or delete files. I don't know if a hard drive should be used differently but at home that is how we would like to use it.

---

