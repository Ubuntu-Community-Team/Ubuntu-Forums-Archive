---
title: "NTFS drive not recognized"
date: 2006-06-23
forum: Desktop Environments
---

### Post by bluezdood on 2006-06-23
I had posted this before but got no response after a while.  Here's the deal, I've installed Ubuntu before and had a successful dual boot laptop.  The last time I installed Ubuntu it recognized my NTFS drive and would allow me to read it.  Since that time I got rid of Ubuntu.  Now I have decided I want to permanently leave my laptop as dual boot.  However, when I installed Ubuntu this time, it didn't recognize my NTFS drive at all.  When I try to access it from the file browser it says I can't because I don't have the proper permissions.  Here's the output of sudo fdisk -l  and cat /etc/fstab

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8193    65810241    7  HPFS/NTFS
/dev/hda2            8194       11996    30547597+  83  Linux
/dev/hda3           11997       12161     1325362+   5  Extended
/dev/hda5           11997       12161     1325331   82  Linux swap / Solaris

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Can someone please help me fix this so the NTFS drive shows up readable in Ubuntu?

---

### Post by x64Jimbo on 2006-06-23
Well, your fstab is not setting up your NTFS partition to be read on boot. I'd recommend booting your Ubuntu LiveCD and capturing the fstab file that it writes, and overwrite your current one with that.

---

### Post by bohboh on 2006-06-23
Here's mine which allows me to browse my ntfs drive (i created the directory /windows/mp3):

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sdb1	/windows/mp3	ntfs	nls=utf8,umask=0222	0	0

```

So i would guess yours needs to be
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda1	/some/mount	ntfs	nls=utf8,umask=0222	0	0

```

Remember to change /some/mount to yours.

then do 

sudo mount -a

---

### Post by aysiu on 2006-06-23
Full instructions to get what bohboh has:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

