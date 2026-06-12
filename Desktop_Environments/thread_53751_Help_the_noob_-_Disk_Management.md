---
title: "Help the noob - Disk Management??"
date: 2005-08-02
forum: Desktop Environments
---

### Post by mpedrummer on 2005-08-02
OK, I give up.

Where's the "disk management" tool?  I have several drives in the machine, and I want to mount them, etc, but...I can't find the darn things.

The "computer" area under the places list only shows mounted devices...where can I find the unmounted ones in gnome?  I had temporarily installed Kubuntu, and easily found things there, but basically decided that the Gnome version was more polished and easier on the eyes (sorry, Kubuntu guys!) so I switched back to Ubuntu.

Thanks
MPEDrummer

---

### Post by Sam on 2005-08-02
To list your partitions, open a terminal and type
```
sudo fdisk -l
```
To edit a disc, type (repace hda with your drive)
```
sudo cfdisk /dev/hda
```

Maybe there is a GUI tool, I don't know any.

---

### Post by mpedrummer on 2005-08-02
Correct me if I'm wrong, but wouldn't that erase/reformat the drive?

---

### Post by Sam on 2005-08-02
The second command, yes.

For mounting your partitions, you need to edit the file /etc/fstab.

If you don't understand the syntax,
```
$ man fstab
```otherwise ask here.

---

### Post by Irony on 2005-08-02
The actual instructions can be found at;

[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

I'm new to linux but found it easy enough. Basically the first instruction makes a folder called windows the second instruction then mounts the partition (which is determined from the sudo fdisk -l command). The third instruction unmounts the partition.

The windows folder can be deleted once it is unmounted by typing;

*sudo rmdir /media/windows*

---

### Post by mpedrummer on 2005-08-02
OK, manually editing fstab it is...no offense, but it's stuff like this that's keeping Linux away from desktop users.

Before I start a flame war, however, I do have one other question about all this...the drives in question are reiserfs 3.6.  I noticed that Ubuntu installs reiser4, does anyone know if it's backwards compatible?

MPEDrummer

---

### Post by Takis on 2005-08-02
[QUOTE=mpedrummer]OK, manually editing fstab it is...no offense, but it's stuff like this that's keeping Linux away from desktop users.[/QUOTE]
Do you think so? I dunno so much about how important that is - most desktop users have no idea what partitions are, nor do they need to.

---

### Post by neighborlee on 2005-08-02
[QUOTE=Takis]Do you think so? I dunno so much about how important that is - most desktop users have no idea what partitions are, nor do they need to.[/QUOTE]

tell that to windowsXP users or mac users for whom such things are easy as pie.

not all distros are created equal and   well..ubuntu as NICE and cordial as it is is not 'yet' in the 'ease of use' department when it comes to being compared to the ease of use of other popular operating systems..if that is our goal , and ubuntu claims it is, then our object is not yet met, but im sure well on its way if you believe the wikis ;-)

cheers
nl

---

### Post by mpedrummer on 2005-08-02
I certainly didn't mean to imply that Ubuntu is a poor distro, quite the contrary.  But it is this type of thing that pops up a lot in the Linux world...you can do it, and it's certainly a powerful feature, but damned if you can find it sometimes.

I'm about to try this (I'll let you know how it goes) but it seems to me like this is one of the assumptions in the Linux world: all the tutorials I found either assumed I already knew a heck of a lot about it, or just glossed over it like a feature I'd never need.

MPEDrummer

---

### Post by mpedrummer on 2005-08-02
OK, no luck so far:

When I try to mount the partition /dev/hdg1, I get the following output:
```
mount: wrong fs type, bad option, bad superblock on /dev/hdg1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Here's the output from fdisk -l:
```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4677    37567971   83  Linux
/dev/hda2            4678        4865     1510110    5  Extended
/dev/hda5            4678        4865     1510078+  82  Linux swap / Solaris

Disk /dev/hdg: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1       24321   195358401   83  Linux

Disk /dev/hdh: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1   *           1       24321   195358401   83  Linux

Disk /dev/sda: 300.0 GB, 300069052416 bytes
1 heads, 63 sectors/track, 9302736 cylinders
Units = cylinders of 63 * 512 = 32256 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2     9206351   290000000   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
1 heads, 63 sectors/track, 9302736 cylinders
Units = cylinders of 63 * 512 = 32256 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2     9302737   293036184   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.

```

sda and sdb are both part of a failed RAID5, which is another matter entirely.  I'm disgruntled about that.

Here's my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdg1       /mnt/hdg        reiserfs        defaults,errors-remount-ro 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

For now I'm going to delete the line relating to hdg1.

Now for the "horrible truth" part.  It's half of a mirrored (soft) RAID.  These drives come from a Mandrake server I had set up, and I'm trying to migrate to Ubuntu at the moment.  Suse simply mounted half the drive, so I'm assuming that it isn't a problem here?  Or does that change things entirely?  I have the other half.

My backup plan here is to use my Suse laptop to transfer the files, once I get the hardware RAID5 rocking.  I'll just use a firewire case, or something.

Anyway, all help is appreciated.

Thanks
MPEDrummer

---

### Post by mpedrummer on 2005-08-04
bump.

Sorry to pester, but I'm really not getting anywhere with this on my own...I do have one idea, but I'm not sure it'll work.

MPEDrummer

---

### Post by Takis on 2005-08-07
I'm not too sure on this, but why are you using reiserfs for your ex-Mandrake partition? I was under the impression Mandrake used ext3.

---

### Post by mpedrummer on 2005-08-09
Mandrake was my first effort into Linux, apart from some really pared-down red hat 9 boxes I used at work.  A friend of mine had told me that reiserfs was the sh*t, so I decided to try it.

Truth be told, I really like the filesystem, at least as compared to NTFS.  It has its shortcomings, I suppose, but it's quite stable, and I've never had problems with it, even through crashes, etc.  Can't say the same for NTFS, that's for sure...sigh.

Anyway, I still haven't really resolved this issue...I'm currently waiting for Seagate to send me new drives from under warranty...and this week I'm installing laminate wood flooring in my living room and dining room, so I'm busy enough that it's not an issue.

But it will be :)

Thanks for the help so far
MPEDrummer

---

