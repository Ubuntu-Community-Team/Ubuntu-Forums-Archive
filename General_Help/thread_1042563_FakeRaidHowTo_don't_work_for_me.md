---
title: "FakeRaidHowTo don't work for me"
date: 2009-01-17
forum: General Help
---

### Post by psychok9 on 2009-01-17
"https://help.ubuntu.com/community/FakeRaidHowto" don't work for me :(
I've installed Ubuntu on ext3 raid partition (Intel ICH10) but I'm lock on

```

ubuntu@ubuntu:/dev/mapper$ sudo mount isw_bbbbdhcghe_S3203 /target
ubuntu@ubuntu:/dev/mapper$ sudo mount --bind /dev /target/dev
ubuntu@ubuntu:/dev/mapper$ sudo mount -t proc proc /target/proc
ubuntu@ubuntu:/dev/mapper$ sudo mount -t sysfs sys /target/sys
ubuntu@ubuntu:/dev/mapper$ sudo chroot /target
-- grub and dmraid already installed from apt-get --
root@ubuntu:/# grub --no-curses
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/isw_bbbbdhcghe_S320
device (hd0) /dev/mapper/isw_bbbbdhcghe_S320
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> 

```
Ubuntu 8.10 x86_64.

---

### Post by caljohnsmith on 2009-01-17
Mistake, sorry.

---

### Post by fjgaude on 2009-01-17
Are you trying to boot into Ubuntu from a fakeRAID drive-pair, raid1?

---

### Post by psychok9 on 2009-01-17
> **fjgaude said:**
> Are you trying to boot into Ubuntu from a fakeRAID drive-pair, raid1?

I've raid 0 (stripe).

---

### Post by fjgaude on 2009-01-18
As far as I know, there is no way to boot into Linux using raid0, except using somekind of driver for the raid before the OS starts to load. Windows does it this way because of the BIOS setup just for it and a driver disk to load into Windows during install. I think the HOW-TOs all show how to use raid1, mirror, to boot into Ubuntu. Sorry about that.

---

### Post by psychok9 on 2009-01-18
> **fjgaude said:**
> As far as I know, there is no way to boot into Linux using raid0, except using somekind of driver for the raid before the OS starts to load. Windows does it this way because of the BIOS setup just for it and a driver disk to load into Windows during install. I think the HOW-TOs all show how to use raid1, mirror, to boot into Ubuntu. Sorry about that.

I've fixed the problem with "Ubuntu Alternate CD 8.10" (very annoying, Live CD is very useful and nice during the Ubuntu installation), it has a Serial ATA Raid driver integreated on the cd (but I can't understand why it's not possibile with the "Normal LiveCD".). On Windows Vista/7, the driver is builded with the setup (like the Ubuntu Alternate cd).

But now I've another problem:
[[IMG]http://img218.imageshack.us/img218/4599/erroregpartedmc8.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=erroregpartedmc8.jpg)[[IMG]http://img218.imageshack.us/img218/3992/gpartedmd6.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=gpartedmd6.jpg)

Translated is: The Kernel can't re-read the partitions table of following devices.
Because of this, it's allowed a limited access. Unmount all partitions mounted on the device for a complete access.

Any advice?
This is my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/mapper/isw_eahdfdefff_raid2
UUID=0827ef28-e918-471a-b0c4-f4f9ca3f4d33 /               ext3    relatime,errors=remount-ro 0       1

# /dev/mapper/isw_eahdfdefff_raid6
UUID=6b70c246-696f-4fec-ad97-8f4446d979fa /home           ext3    relatime        0       2

# /dev/mapper/isw_eahdfdefff_raid1
UUID=EE1E91571E911A23 /media/windows7 ntfs    defaults,umask=000,gid=00 0       0

# /dev/mapper/isw_eahdfdefff_raid5
UUID=c0a43d71-ef19-4a67-b661-a25d5625e7cf none            swap    sw              0       0

/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sda1
UUID=54608D2B608D14C0 /media/storage ntfs     defaults,umask=000,gid=00 0       0
```

---

