---
title: "name of desktop mounted volume corrupt"
date: 2006-11-30
forum: Desktop Environments
---

### Post by coldrick on 2006-11-30
In Edgy Gnome: all of a sudden, one of my fstab-mounted drives shows a garbage name. If I drag the desktop icon into gedit, it shows:

x-nautilus-desktop:///ody%3E%0A%0A%3C%2Fhtm.volume

instead of the correct:

x-nautilus-desktop:///Data.volume

Nothing has changed in /etc/fstab, and the volume itself is fine, it's just the name that's become junk.

I've tried a reboot, didn't fix it. How do I fix this?

Thanks and regards,
David

---

### Post by taurus on 2006-11-30
What are the outputs of these two commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by coldrick on 2006-11-30
fdisk -l gives:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        3830    30716280    7  HPFS/NTFS
/dev/sda3            3831       12161    66918757+   f  W95 Ext'd (LBA)
/dev/sda5            6263        6588     2618563+  82  Linux swap / Solaris
/dev/sda6            6589       10054    27840613+   b  W95 FAT32
/dev/sda7           10055       12161    16924446   83  Linux
/dev/sda8            3831        6262    19534977   83  Linux

Partition table entries are not in disk order


Note that sda6 is the volume in question.

fstab looks like:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=3f6bcd4b-c31e-4f92-8b5a-5642cbd4e6df /               reiserfs notail          0       1
# /dev/sda7
UUID=4a680cfb-46ae-4fcd-9052-764ea4186972 /home  jfs  defaults  0       2
# /dev/sda1
# UUID=07D5-080D  /media/sda1  vfat defaults,utf8,umask=007,gid=46 0  1
# /dev/sda2
UUID=E0C8E627C8E5FC22 /media/Windows  ntfs defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=4305-863B  /media/Data vfat rw,users,auto,uid=1000 0 0
# /dev/sda5
UUID=919c2b64-9724-4f9b-bc33-c4db9882337a none  swap sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Regards,
David

---

### Post by taurus on 2006-11-30
Well, you can change the /dev/sda6 from current entry to make it look something like this!

```

/dev/sda6   /media/Data   vfat   iocharset=utf8,umask=000   0   0

```
Reboot and see if it's working again...

---

### Post by coldrick on 2006-11-30
No change.

---

### Post by coldrick on 2006-11-30
Any other thoughts? Configuration Editor doesn't appear to provide a way of changing these names

---

### Post by coldrick on 2006-12-05
Fixed. Went away after several days/ reboots/ phases of the moon. Dunno why it came, dunno why it went.

---

### Post by billstei on 2006-12-25
Same thing here today.  Name of fat32 volume is corrupt in Places menu and in Nautilus.  Booting (is dual boot) into Win2k displays the volume name okay.

---

### Post by cmcginty on 2006-12-27
Same for me too. Ever since installation my FAT32 volume is labeled as: [FONT="Courier New"]**/noexecute=**[/FONT]

I noticed that I can find this mount name in a file located at: [FONT="Courier New"]/home/user/.nautilus/metafiles/x-nautilus-desktop\:%2F%2F%2F.xml [/FONT]

---

### Post by billstei on 2006-12-31
I found where the corrupt volume name is stored, but I am unsure as to how it got that way, or whether it is safe to edit it.  In the file /dev/.udev/db/block@hda@hda7 I see the following (I replaced the actual garbage text with the word GARBAGE to avoid pasting ctrl characters into the forum post):

N:hda7
S:disk/by-id/ata-SAMSUNG_SP8004H_0415J1FT943191-part7
S:disk/by-path/pci-0000:00:02.5-ide-0:0-part7
S:disk/by-uuid/3FEB-065A
S:disk/by-label/GARBAGE
M:3:7
E:ID_TYPE=disk
E:ID_MODEL=SAMSUNG_SP8004H
E:ID_SERIAL=0415J1FT943191
E:ID_REVISION=QW100-60
E:ID_BUS=ata
E:ID_PATH=pci-0000:00:02.5-ide-0:0
E:ID_FS_USAGE=filesystem
E:ID_FS_TYPE=vfat
E:ID_FS_VERSION=FAT32
E:ID_FS_UUID=3FEB-065A
E:ID_FS_LABEL=GARBAGE
E:ID_FS_LABEL_SAFE=GARBAGE

Comparing this to block@hda@hda6 the three GARBAGE entries are the only significant difference.  Can I, or should I, just edit this file?  If I delete it will it be rebuilt (correctly)?  I think it is safe to say that some sort of bug report could be submitted for udev, or gnome-volume-manager, or...what??

---

### Post by billstei on 2006-12-31
I tried editing block@hda@hda7 but after reboot the file is regenerated with the (same) corrupt volume name(s).  As I understand it, the file is produced via udev rules, therefore either they are buggy, or the programs they rely on are.

---

### Post by cmcginty on 2007-02-06
I am having this same problem ever since I installed Ubuntu. How do I fix this??

Here is a screen shot: ('/noexecute' should be 'sda1')
[ATTACH]24639[/ATTACH]

---

### Post by billstei on 2007-02-14
I compiled and am running my own kernel, 2.6.20, and the problem seems to be resolved now.

---

