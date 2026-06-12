---
title: "USB Ports (Except Printer) No Longer Mount"
date: 2006-06-06
forum: Desktop Environments
---

### Post by jwh400 on 2006-06-06
I have seen problems like this in other threads but am unable to make the suggestions given work for me. Flash drive, 6 in 1 card reader, CD ROM, and external drive will no longer mount after 5 months of working just fine. All show as being detected but attempting to open any will result in;

[I]Unable to mount the selected vulume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superblock on /dev/sdf,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdf,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount[/I]

The output from sudo fdisk l is;

*Unable to open l*

the output of cat /etc/fstab is;

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/I]

I don't understand what the "errors" in dev/hda1 mean or how to correct them. Also the cdrom and floppy say "noauto", is this why they won't mount? Being signed in as root also makes no difference if that's important. The printer connects by USB and it is working fine. ](*,)
Since my external won't mount either I've spent the last several hours backing up files to Rapidshare in case my problem is serious.:roll: I also checked out the link at psychocats.net/ubuntu/mountwindows.php but didn't understand what they were talking about. It seemed to be about mounting Windows partitions but I have nothing from Microsoft on this computer. Ubuntu is the only operating system I use.
Thanks for any and all help.
:)

---

### Post by Vati-Khan on 2006-06-06
give us 

*sudo fdisk -l /dev/sdf*

please. Maybe try

[I]sudo mkdir /media/sdfX
sudo mount /dev/sdfX /media/sdfX[/I]

where X is the partition's number -> see fdisk -l output probably 1;-)

and make sure these conditions are met 

       · device is not already mounted according to /etc/mtab and /proc/mounts

       · if the mount point already exists, there is no device already mounted
         at it and the directory is empty

       · device   is   removable   (USB,   FireWire,   or   MMC   device,   or
         /sys/block/drive/removable is 1) or whitelisted in /etc/pmount.allow.

       · device is not locked

---

### Post by jwh400 on 2006-06-06
When entering sudo fdisk -l /dev/sdf  I get;

Disk /dev/sdf: 1039 MB, 1039663104 bytes
256 heads, 32 sectors/track, 247 cylinders
Units = cylinders of 8192 * 512 = 4194304 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         248     1015280    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 255, 32) logical=(247, 223, 32)

>  Maybe try

[I]sudo mkdir /media/sdfX
sudo mount /dev/sdfX /media/sdfX[/I]

where X is the partition's number -> see fdisk -l output probably 1 
I'm not sure what those commands do so I don't know what I'd be trying.
 
When entering /etc/mtab I get "permission denied". I'm signed in as root again.

When entering /proc/mounts I get "permission denied".

I went ahead and tried *sudo mkdir /media/sdfX  and  *[I]sudo mkdir /media/sdfX

[/I]Now I have an icon on my desktop named sdf1 and apparently a new device labled sdf1. How do I get rid of this?

---

### Post by jwh400 on 2006-06-06
I right clicked on sdf1 and selected "Unmount" and it seems to be gone. What was the purpose of that?

---

### Post by jwh400 on 2006-06-06
In my first post I left out a hyphen so I ran sudo fdisk -l again and got;

[i]Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14759   118551636   83  Linux
/dev/hda2           14760       14946     1502077+   5  Extended
/dev/hda5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    c  W95 FAT32 (LBA)[/i]


the output of cat /etc/fstab is;

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

[/I]I see the mount point for the floppy and CD ROM is media but the external harddrive isn't showing at all. If any additional info is needed I'll try to find it.:)

---

### Post by jwh400 on 2006-06-08
Could someone please tell me what "defaults,errors=remount-ro" in hda1 means?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Since nothing will mount I'm unable to backup anything so I'm afraid to do much trial and error. I returned to psychocats.net/ubuntu/mountwindows.php and read through it a few more times but since they're talking about Windows partitions I'm afraid to try anything there because I don't understand what it has to do with this but in other threads where people have this sort of problem that is the site they're refered to. Do I unmount hda1 and remount it? Do I do the same with hdc and fd0? The external and flashdrive aren't even showing (they're both connected) so what would I do there?

A fresh install is out of the question until I can move my files somewhere. Once I'm able to do that I'd like to upgrade to Dapper Drake but I'm at a standstill right now and at my wits end. Is there anyone that knows anything at all about this? 
:(

---

