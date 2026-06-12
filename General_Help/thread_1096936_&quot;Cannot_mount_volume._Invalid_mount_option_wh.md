---
title: "&quot;Cannot mount volume. Invalid mount option when attempting to mount the volume&quot;"
date: 2009-03-15
forum: General Help
---

### Post by Rootbrian on 2009-03-15
Attached is the screenshot of the error (as is in the title) i'm getting each time I mount any USB drive. It's all pointing to the [FONT="Courier New"]/media/cdrom[/FONT] and I can't seem to change it. I did try some commands after looking it up and managed to mount it. Now after I unplugged it, it's back to the same old story.

I need some help getting this "CD-ROM/read-only Syndrome" solved and cured.

Maybe another patch needs to be written or something.

I'm using Ubuntu 8.04.2 (hardy), Kernel version 2.6.24-23-generic and GNOME 2.22.3.

[Status updates]
1. I'm going to try a Reboot and see if anything changes.
2. Reboot done, now getting information from "dmesg | tail" before plugging in USB drive...

sony@sony-desktop:~$ dmesg | tail
[   52.720631] audit(1237137661.741:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5182 profile="/usr/sbin/cupsd" namespace="default"
[   55.230147] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   55.231785] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.236556] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   58.635577] NET: Registered protocol family 17
[   58.691980] [drm] Initialized drm 1.1.0 20060810
[   58.703435] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   58.703454] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   58.704376] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   72.476210] eth0: no IPv6 routers present

Now after plugging in 4GB CF MicroDrive in USB memory card reader...

sony@sony-desktop:~$ dmesg | tail
[  434.423664] sd 3:0:0:0: [sdc] Write Protect is off
[  434.423677] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  434.423682] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  434.425157] sd 3:0:0:0: [sdc] 7999488 512-byte hardware sectors (4096 MB)
[  434.426160] sd 3:0:0:0: [sdc] Write Protect is off
[  434.426173] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  434.426178] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  434.426192]  sdc: sdc1
[  435.661312] UDF-fs: No partition found (1)
[  435.849350] ISOFS: Unable to identify CD-ROM format.

***CAN ANYBODY EXPLAIN THIS?!?!*** It's been happening for a while and haven't figured it out. I'm not a programmer and I don't have any hacking skills to fix it up.

---

### Post by Rootbrian on 2009-03-15
> **Rootbrian said:**
> Attached is the screenshot of the error (as is in the title) i'm getting each time I mount any USB drive. It's all pointing to the [FONT="Courier New"]/media/cdrom[/FONT] and I can't seem to change it. I did try some commands after looking it up and managed to mount it. Now after I unplugged it, it's back to the same old story.

I need some help getting this "CD-ROM/read-only Syndrome" solved and cured.

Maybe another patch needs to be written or something.

I'm using Ubuntu 8.04.2 (hardy), Kernel version 2.6.24-23-generic and GNOME 2.22.3.

[Status updates]
1. I'm going to try a Reboot and see if anything changes.
2. Reboot done, now getting information from "dmesg | tail" before plugging in USB drive...

sony@sony-desktop:~$ dmesg | tail
[   52.720631] audit(1237137661.741:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5182 profile="/usr/sbin/cupsd" namespace="default"
[   55.230147] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   55.231785] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.236556] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   58.635577] NET: Registered protocol family 17
[   58.691980] [drm] Initialized drm 1.1.0 20060810
[   58.703435] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   58.703454] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   58.704376] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   72.476210] eth0: no IPv6 routers present

Now after plugging in 4GB CF MicroDrive in USB memory card reader...

sony@sony-desktop:~$ dmesg | tail
[  434.423664] sd 3:0:0:0: [sdc] Write Protect is off
[  434.423677] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  434.423682] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  434.425157] sd 3:0:0:0: [sdc] 7999488 512-byte hardware sectors (4096 MB)
[  434.426160] sd 3:0:0:0: [sdc] Write Protect is off
[  434.426173] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[  434.426178] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  434.426192]  sdc: sdc1
[  435.661312] UDF-fs: No partition found (1)
[  435.849350] ISOFS: Unable to identify CD-ROM format.

***CAN ANYBODY EXPLAIN THIS?!?!*** It's been happening for a while and haven't figured it out. I'm not a programmer and I don't have any hacking skills to fix it up.

Also got another screenshot attached with the error from plugging in my 128MB USB flash drive. This was with my microdrive plugged into the USB memory card reader.

[Message from [FONT="Courier New"]dmesg | tail[/FONT] with MicroDrive unplugged]

sony@sony-desktop:~$ dmesg | tail
[ 3318.340622] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 3318.342471] sd 6:0:0:0: [sdc] 248928 512-byte hardware sectors (127 MB)
[ 3318.343361] sd 6:0:0:0: [sdc] Write Protect is off
[ 3318.343374] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 3318.343379] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 3318.343393]  sdc: sdc1
[ 3318.399213] sd 6:0:0:0: [sdc] Attached SCSI disk
[ 3318.399316] sd 6:0:0:0: Attached scsi generic sg4 type 0
[ 3319.378591] UDF-fs: No partition found (1)
[ 3319.450407] ISOFS: Unable to identify CD-ROM format.

With MicroDrive plugged into USB memory card reader...

sony@sony-desktop:~$ dmesg | tail
[ 3451.683045] sd 7:0:0:0: [sdd] Write Protect is off
[ 3451.683057] sd 7:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 3451.683063] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 3451.686278] sd 7:0:0:0: [sdd] 7999488 512-byte hardware sectors (4096 MB)
[ 3451.687667] sd 7:0:0:0: [sdd] Write Protect is off
[ 3451.687679] sd 7:0:0:0: [sdd] Mode Sense: 03 00 00 00
[ 3451.687683] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[ 3451.687697]  sdd: sdd1
[ 3451.708710] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[ 3451.708811] sd 7:0:0:0: Attached scsi generic sg5 type 0

EVERYTHING IS WORKING!! What the HELL?!?! This is unexplainable.

---

### Post by taurus on 2009-03-15
How about an output of 

```
sudo fdisk -l
```

---

### Post by Rootbrian on 2009-03-15
> **taurus said:**
> How about an output of 

```
sudo fdisk -l
```

Output is from 3 USB disks plugged in.

Only the MicroDrive is plugged in:

sony@sony-desktop:~$ sudo fdisk -l
[sudo] password for sony: 

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x279a2799

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4910    39432928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4911        9834    39552030   83  Linux
/dev/sda3            9835        9964     1044225   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10021001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdd: 4095 MB, 4095737856 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002ac75a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         497     3992121    6  FAT16

MicroDrive unplugged, replugged in:

sony@sony-desktop:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x279a2799

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4910    39432928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4911        9834    39552030   83  Linux
/dev/sda3            9835        9964     1044225   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10021001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdc: 4095 MB, 4095737856 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002ac75a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         497     3992121    6  FAT16

Now with 128MB USB flash drive plugged in:

sony@sony-desktop:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x279a2799

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4910    39432928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            4911        9834    39552030   83  Linux
/dev/sda3            9835        9964     1044225   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10021001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdc: 127 MB, 127451136 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x095ee605

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          15      120456    6  FAT16


Still can't mount because it thinks it's a CD-ROM drive. Any way to get past it?

I could post dmesg | tail for all 3 devices (memory card reader with media, usb hard disk, usb flash drive)

Additional information:

When manual mounting with incorrect vfat code, it force mounts as read-only (CD-ROM-style).

Still, it's the same problem. I can't create or move files.

---

### Post by taurus on 2009-03-15
Which drive do you plan to mount anyway?  What does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by Rootbrian on 2009-03-16
> **taurus said:**
> Which drive do you plan to mount anyway?  What does your /etc/fstab look like?

```
cat /etc/fstab
```

With no USB drives plugged in:

[FONT="Courier New"][FONT="Fixedsys"]sony@sony-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ec2fbc81-44da-4a93-9565-bf72b40301b9 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=ff0d975b-96a7-4edf-a94c-6cb7f8a650a5 none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[/FONT][/FONT]

With 3 USB drives (3.2GB USB HDD using IDE2USB cable works fine) plugged in:
[FONT="Fixedsys"]
sony@sony-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ec2fbc81-44da-4a93-9565-bf72b40301b9 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=ff0d975b-96a7-4edf-a94c-6cb7f8a650a5 none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[/FONT]

Now with USB HDD unplugged:

[FONT="Fixedsys"]sony@sony-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ec2fbc81-44da-4a93-9565-bf72b40301b9 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=ff0d975b-96a7-4edf-a94c-6cb7f8a650a5 none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[/FONT]

---

### Post by taurus on 2009-03-16
> **Rootbrian said:**
> 

[FONT="Fixedsys"]sony@sony-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ec2fbc81-44da-4a93-9565-bf72b40301b9 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=ff0d975b-96a7-4edf-a94c-6cb7f8a650a5 none            swap    sw              0       0
**[COLOR="DarkRed"]/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/COLOR]**
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[/FONT]

There you go.  You told the system to mount /dev/sdc1 to /media/cdrom0!  Perhaps you meant /dev/scd1 instead of /dev/sdc1.

---

### Post by Rootbrian on 2009-03-16
> **taurus said:**
> There you go.  You told the system to mount /dev/sdc1 to /media/cdrom0!  Perhaps you meant /dev/scd1 instead of /dev/sdc1.

I didn't tell the system to mount it as a CD-ROM, it's doing this to every usb flash drive plugged in I got including any media in the memory card reader.

There's gotta be a way to correct this.

---

### Post by taurus on 2009-03-16
Why don't you edit /etc/fstab and place a # in front of the line for /dev/sdc1 to comment it out?  You need to reboot after modifying /etc/fstab.

```

**[COLOR="Blue"]#[/COLOR]**/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

Just so you know.  If you have two harddrives in your machine, they will be /dev/sda & /dev/sdb so when you insert an external USB drive, it will be /dev/sdc1.  But since you have /dev/sdc1 mount to /media/cdrom0 with udf,iso9660 filesystem in /etc/fstab, it will bomb you out, wrong filesystem.

---

### Post by Rootbrian on 2009-03-16
> **taurus said:**
> Why don't you edit /etc/fstab and place a # in front of the line for /dev/sdc1 to comment it out?  You need to reboot after modifying /etc/fstab.

```

**[COLOR="Blue"]#[/COLOR]**/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

Just so you know.  If you have two harddrives in your machine, they will be /dev/sda & /dev/sdb so when you insert an external USB drive, it will be /dev/sdc1.  But since you have /dev/sdc1 mount to /media/cdrom0 with udf,iso9660 filesystem in /etc/fstab, it will bomb you out, wrong filesystem.

How is this corrected? I haven't a clue why it's happening. USB flash drives/media (fat16/32) should mount to /media/disk (disk2 disk3, volume label, etc), not /media/cdrom.

---

### Post by taurus on 2009-03-16
I am trying to help you to fix the problem and in fact, I even offered you a solution but it looks like you are not going to listen so you do whatever you want then.

---

### Post by heindsight on 2009-03-16
/etc/fstab is a file telling your system where to mount certain devices and with what options. Usually removable drives (except cdroms) are not listed there. Instead they're automatically mounted through HAL

In your /etc/fstab you have a line saying that the device
/dev/sdc1 should be mounted as a cdrom drive at /mnt/cdrom
What's happening is that your usb drive is assigned the name /dev/sdc, the first partition on the drives becomes /dev/sdc1 and then the system tries to mount it as a CDROM with either udf or iso9660 filesystem and fails.

if you remove (comment out) that line from /etc/fstab as taurus suggested, then the drive will be mounted correctly by HAL.

---

### Post by Rootbrian on 2009-03-16
I fixed the problem.

I removed the "/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0" from the /etc/fstab file and saved it, unplugged the memory card reader and usb disk, plugged them back in and it mounts like it did before.

Must've been a glitch with the installation or something else. I only modified the file a few minutes ago before this post.

I just still can't use my USB flash drive yet, it's giving me what you saw in the last screenshot.

---

### Post by Rootbrian on 2009-03-16
> **Rootbrian said:**
> I fixed the problem.

I removed the "/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0" from the /etc/fstab file and saved it, unplugged the memory card reader and usb disk, plugged them back in and it mounts like it did before.

Must've been a glitch with the installation or something else. I only modified the file a few minutes ago before this post.

I just still can't use my USB flash drive yet, it's giving me what you saw in the last screenshot.

Another Dialog box error screenshot attached.

Don't know where the file to edit may be.

---

### Post by heindsight on 2009-03-16
> **Rootbrian said:**
> 
I just still can't use my USB flash drive yet, it's giving me what you saw in the last screenshot.

When your flash drive is automatically mounted, the filesystem label is used as the name of the mountpoint under /media. That error message is complaining about illegal characters in the mountpoint name. plug the drive in and run:
```
sudo blkid
```
to see the labels of all your filesystems.

I suspect you'll have to change the filesystem label to get rid of the error.

---

### Post by mc4man on 2009-03-16
The other possibiliy is you edited the mount point of the usb drive incorrectly thru it's properties (either the volume or drive
The only valid entry if you did so is the mount directory (in /media), not the mount point
Ex.
test is a valid entry
/media/test is not

To ck. run
```
gconf-editor
```
and look under system -> storage for a listing for the usb drive (based on UUID
If it's there right click the mount point entry and choose unset
screen shows an improper entry for usb flash drive

---

### Post by Rootbrian on 2009-03-16
> **heindsight said:**
> When your flash drive is automatically mounted, the filesystem label is used as the name of the mountpoint under /media. That error message is complaining about illegal characters in the mountpoint name. plug the drive in and run:
```
sudo blkid
```
to see the labels of all your filesystems.

I suspect you'll have to change the filesystem label to get rid of the error.

Result from using the code:

[FONT="Fixedsys"]sony@sony-desktop:~$ sudo blkid
[sudo] password for sony: 
/dev/sda1: UUID="C47C0E3F7C0E2CAC" TYPE="ntfs" 
/dev/sda2: UUID="ec2fbc81-44da-4a93-9565-bf72b40301b9" TYPE="ext2" 
/dev/sda3: TYPE="swap" UUID="ff0d975b-96a7-4edf-a94c-6cb7f8a650a5" 
/dev/sdb1: LABEL="40GBSupStor" UUID="D777-CDF3" TYPE="vfat" 
**/dev/sdc1: SEC_TYPE="msdos" UUID="49B1-5206" TYPE="vfat"** The 128MB USB flash drive.
[/FONT]

---

### Post by Rootbrian on 2009-03-16
> **mc4man said:**
> The other possibiliy is you edited the mount point of the usb drive incorrectly thru it's properties (either the volume or drive
The only valid entry if you did so is the mount directory (in /media), not the mount point
Ex.
test is a valid entry
/media/test is not

To ck. run
```
gconf-editor
```
and look under system -> storage for a listing for the usb drive (based on UUID
If it's there right click the mount point entry and choose unset
screen shows an improper entry for usb flash drive

There wasn't an entry shown, but I did unset /media/disk1 and i'll see if it works. SUCCESS! it works and mounts. Testing with memory card reader. Everything is working like it once did before.

Thanks for the help.

---

### Post by Rootbrian on 2009-03-16
I'll be sure to remember to use that editor before posting the problem on the forums. Only posting if I can't fix it would greatly give you all a break. Sorry if I seemed not to be listening.

---

### Post by corq on 2009-03-16
I was running Jaunty Alpha when I discovered this issue after a nightly dist-upgrade (my own peril, I know.)

I cannot comment on your further problem, but when you pointed me to the fstab - a lightbulb went off; I had an entry for the cdrom0; interestingly, I'm on an Acer Aspire One, Netbook. these have no cdroms.

No idea if that's a generic entry, but I remarked-out this entry, this and suddenly the flash drive mounts and is explorable with nautilus.

---

### Post by mc4man on 2009-03-16
> I had an entry for the cdrom0; interestingly, I'm on an Acer Aspire One, Netbook. these have no cdroms.

I think when you install from a usb drive, then an entry is made in fstab for sdb1 or scd1 ect. (also erroneously treating as a 'cd/dvd' drive in many cases.

Well worth checking for after usb installs

---

### Post by Rootbrian on 2009-03-17
I had to reinstall windows and ubuntu cause nothing would play or work on linux (kernel panic every time), nothing would start in windows (XP).

Everything is fine now, i'll check my fstab later on to verify if I have to remove/mark out that entry to restore use of any USB drive other than a CD/DVD-ROM.

It's a good thing I brought this issue up first-hand cause it never existed before 2 days ago thanks to me :)

I saved everybody a whole lotta time.

---

### Post by candtalan on 2009-07-31
i have just installed a 8.04.3 system, not from cd but from a live usb (unetbootin) and the install went well.
However, after the install and updates i then tried a usb stick and got his error.

From this thread I saw to look in fstab and yes, the sdb1 usb stick was trying to mount as a cd.
I commented out the offending line, saved and rebooted, problem solved

---

### Post by ingmarbaus on 2009-10-31
> **taurus said:**
> Why don't you edit /etc/fstab and place a # in front of the line for /dev/sdc1 to comment it out?  You need to reboot after modifying /etc/fstab.

```

**[COLOR=Blue]#[/COLOR]**/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```Just so you know.  If you have two harddrives in your machine, they will be /dev/sda & /dev/sdb so when you insert an external USB drive, it will be /dev/sdc1.  But since you have /dev/sdc1 mount to /media/cdrom0 with udf,iso9660 filesystem in /etc/fstab, it will bomb you out, wrong filesystem.

That does the trick! Thanks a lot!

---

### Post by GGG121 on 2009-11-07
I was having the same problem and this solution worked fine for me! Thank you Ubuntuforums Community!

---

