---
title: "hard drive listings change each bootup"
date: 2008-12-07
forum: General Help
---

### Post by themusicalduck on 2008-12-07
I have my home folder on a separate hard drive to my ubuntu install. For some reason the 'name' of this hard drive changes between either sdd3 or sdb3, which means that sometimes when my computer boots up it can find my home and sometimes it can't, depending on what's in my fstab file. Usually I just have to edit the fstab or reboot until it matches up.

fdisk -l is:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x133aa956

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS
/dev/sda2            9730       19012    74565697+  83  Linux
/dev/sda3           19013       19457     3574462+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7ee1564

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3           11471       30027   149059102+  83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf054f054

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   83  Linux

Disk /dev/sdd: 30.6 GB, 30616363008 bytes
255 heads, 63 sectors/track, 3722 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000b7b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        3721    29888901    7  HPFS/NTFS

Disk /dev/sdg: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       91201   732572001    7  HPFS/NTFS

```

fstab is:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd2
UUID=1f8409c6-40a7-4a48-ad23-ad3c6d735a18 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd3
UUID=47da32ed-adf2-4051-af3d-ec52d5be7248 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb3 /home ext3 nodev,nosuid 0 2

```

It matches as stated here, but sometimes switches.

---

### Post by taurus on 2008-12-07
Instead of using /dev/sdb3 in /etc/fstab for your /home, why not use the UUID.

```
sudo blkid
```

---

### Post by themusicalduck on 2008-12-07
How would I edit the fstab to use the UUID?

Just replacing /dev/sdb3 with it doesn't seem to work.

---

### Post by taurus on 2008-12-07
If you need to edit /etc/fstab, just run

```
gksudo gedit /etc/fstab
```
What is the output of this command from a terminal?

```
sudo blkid
```

---

### Post by themusicalduck on 2008-12-08
sudo blkid:

```
/dev/sdc1: UUID="f509e8a6-0bd0-4240-8c00-fbc4e3a80062" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd3: UUID="9d5ba402-ce4c-4e2a-bd1d-1a90f07a310d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: UUID="3C2F2B07292FF190" TYPE="ntfs" 
/dev/sdb3: UUID="9d5ba402-ce4c-4e2a-bd1d-1a90f07a310d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="46efc3e6-4796-4422-8319-1a9b6d605797" TYPE="swap" 
/dev/sda2: LABEL="Ubuntu" UUID="1f8409c6-40a7-4a48-ad23-ad3c6d735a18" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="47da32ed-adf2-4051-af3d-ec52d5be7248" 
/dev/sdd1: UUID="4EC8E9B0C8E9968D" LABEL="Stuff" TYPE="ntfs" 
/dev/sde1: SEC_TYPE="msdos" LABEL="TOOLS" UUID="8346-B83A" TYPE="vfat" 
/dev/sdi1: UUID="4A5CB3EC5CB3D145" LABEL="FreeAgent Drive" TYPE="ntfs" 

```

---

### Post by themusicalduck on 2008-12-08
bump

---

### Post by logos34 on 2008-12-08
> **themusicalduck said:**
> sudo blkid:

[CODE]/dev/sdc1: UUID="f509e8a6-0bd0-4240-8c00-fbc4e3a80062" SEC_TYPE="ext2" TYPE="ext3" 
[COLOR="Red"]/dev/sdd3: UUID="9d5ba402-ce4c-4e2a-bd1d-1a90f07a310d" SEC_TYPE="ext2" TYPE="ext3"[/COLOR] 
/dev/sda1: UUID="3C2F2B07292FF190" TYPE="ntfs" 
[COLOR="Red"]/dev/sdb3: UUID="9d5ba402-ce4c-4e2a-bd1d-1a90f07a310d" SEC_TYPE="ext2" TYPE="ext3" [/COLOR]


blkid reads from the /etc/blkid.id file--still lists two /home.  Try 

sudo blkid -c cachefile

should show only one (what its currently using).  Then maybe clean it up with 

sudo blkid -c /dev/null

edit fstab:

> # /dev/sdb3 
[COLOR="Blue"]9d5ba402-ce4c-4e2a-bd1d-1a90f07a310d[/COLOR] /home ext3 nodev,nosuid 0 2

reboot.  see if that works

---

### Post by themusicalduck on 2008-12-08
That didn't seem to work, if I edit my fstab to reflect that, it can't find the home partition.

Basically it says it can't find it, says something about not being able to read the superblock and then tries to do a scandisk. I can still boot in, but it seems to make or use another home folder using fresh install defaults.

Is it possible that it's getting confused with the home folder originally created by the installation and the home folder stored on my other drive?

---

### Post by themusicalduck on 2008-12-09
bump

---

### Post by logos34 on 2008-12-09
> **themusicalduck said:**
> Is it possible that it's getting confused with the home folder originally created by the installation and the home folder stored on my other drive?

so you're saying you made a copy/image of your /home and stored it here:
> 

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf054f054

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   83  Linux

???

if that's the case, then the partition UUID is preserved, which would explain the mixup...Disconnect the drive or move the partition to your external drive, disconnect and reboot and see if that fixes it

---

### Post by themusicalduck on 2008-12-09
No the home partition is stored on:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7ee1564

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3           11471       30027   149059102+  83  Linux

Basically what I did, was I reinstalled Ubuntu, but I kept a backup of my old home folder on that drive. After reinstalling Ubuntu, I edited the fstab to link home to that drive.

So you think if I disconnect my home drive, restart, shut down and reconnect it again? It will refresh the UUIDs and stop mixing things up?

---

### Post by logos34 on 2008-12-09
ok, so it's the other way around.  If the copy of /home is stored on the 250 gb drive, disconnect that one.  Edit fstab as mentioned above.  What's happining is linux is scanning for mountable partitions at boot up and finding two with the same uuid, and it's confused (wouldn't you be?).  :)

good luck

---

### Post by themusicalduck on 2009-01-10
I know this thread is pretty old, but my problem seemed to fix itself and so didn't need to follow your steps. Except it seems to have come back now :/

When I disconnect the 250 and start up the computer, how exactly am I meant to edit the fstab? If the 250 isn't connected then I can't find out what partition I am meant to point /home to in the fstab.

I tried running ubuntu without the 250 connected, then restarted with it connected, and did the same with the 80. I even ran ubuntu with no drives connected at least once, and then restarted with them all connected again. The problem still happens.

It seems to be affecting grub too as in I can't boot into any OS apart from ubuntu because I can't edit the menu.lst to reflect the ever changing fdisk listing.

---

### Post by logos34 on 2009-01-11
boot from the live cd and fix it.  Generate new UUIDs for the new /home (sdc1) on the 80 GB, as well as for the old home on sdb3 (250 gb). 

sudo tune2fs -U random /dev/sdc1

sudo tune2fs -U random /dev/sdb3

check with 

sudo blkid

Mount your / partition, create a mountpoint for old home and edit /etc/fstab.

sudo mkdir /media/ubuntu

sudo mount -t ext3 /dev/sda2 /media/ubuntu

sudo mkdir /media/ubuntu/media/oldhome

gksudo gedit /media/ubuntu/etc/fstab

> # /dev/sdc1
UUID=[COLOR="Red"]new-uuid[/COLOR] **/home ext3 relatime 0 2**
# /dev/sdb3 (old /home on 250 GB)
UUID=[COLOR="Red"]new-uuid[/COLOR] **/media/oldhome ext3 defaults 0 2**


Add: also, make sure the 'kernel' line in /boot/grub/menu.lst is using 'root=**UUID=1f8409c6-40a7-4a48-ad23-ad3c6d735a18**' format...that should prevent confusion with changing drive letters

---

### Post by themusicalduck on 2009-01-11
EDIT: fixed it.. don't bother reading this post.

I replaced the /dev/sdb3 /home ext3 nodev,nosuid 0 2 line in fstab with the lines that you suggested and added the UUIDs to them, but still it comes up with the recovery shell on bootup.

Though using sudo tune2fs -U random /dev/sdc1 did come up with an error message, I check blkid and the UUIDs were actually different. EDIT: (looking at blkid again they aren't actually different at all..)

Though your comments were a little confusing "# /dev/sda3 (old /home on 250 GB)" as the 250 partition is not my old home but is my current home, but I tried switching the UUIDS around and it made no difference either way.

Though considering now that the UUIDS are now different, could I assume that it won't get confused anymore and can use the same fstab that I had before?

This is now what my fstab says

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=d8adf942-7008-4329-aa22-f9b3d62e41fe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=47da32ed-adf2-4051-af3d-ec52d5be7248 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdc2
UUID=28522AF05E631137 /home ext3 relatime 0 2
# /dev/sda3 (old /home on 250 GB)
UUID=9d5ba402-ce4c-4e2a-bd1d-1a90f07a310d /media/oldhome ext3 defaults 0 2
```

fdisk says:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x133aa956

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS
/dev/sda2            9730       19012    74565697+  83  Linux
/dev/sda3           19013       19457     3574462+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7ee1564

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11470    92132743+   7  HPFS/NTFS
/dev/sdb3   *       11471       30027   149059102+  83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeeb8536a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6324    50797498+  af  Unknown
/dev/sdc2            6325        9729    27350662+   7  HPFS/NTFS

Disk /dev/sdd: 30.6 GB, 30616363008 bytes
255 heads, 63 sectors/track, 3722 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000b7b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        3721    29888901    7  HPFS/NTFS

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       91201   732572001    7  HPFS/NTFS

```

and blkid says:

```
/dev/sdc1: UUID="79B53762387AA91B" LABEL="OSX" TYPE="hfsplus" 
/dev/sda1: UUID="3C2F2B07292FF190" TYPE="ntfs" 
/dev/sdb1: UUID="0DB5C9E626D4A7EE" LABEL="Stuff" TYPE="ntfs" 
/dev/sdb3: UUID="9d5ba402-ce4c-4e2a-bd1d-1a90f07a310d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="9d5ba402-ce4c-4e2a-bd1d-1a90f07a310d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="4EC8E9B0C8E9968D" LABEL="Stuff" TYPE="ntfs" 
/dev/sda2: UUID="d8adf942-7008-4329-aa22-f9b3d62e41fe" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="47da32ed-adf2-4051-af3d-ec52d5be7248" 
/dev/sdc2: UUID="28522AF05E631137" LABEL="Windows 7" TYPE="ntfs" 
/dev/sde1: UUID="4A5CB3EC5CB3D145" LABEL="FreeAgent Drive" TYPE="ntfs" 

```

Also editing menu.lst as root=UUID="UUID" comes up with the error message 'Device string unrecognised'

For example I have one entry as

title		Windows 7
root=UUID=28522AF05E631137
savedefault
makeactive
map		(hd1) (hd2)
map		(hd2) (hd1)
chainloader	+1

None of the entries that I edited work.

Thanks for helping me out so much so far, this seems to be getting turning into a pretty complicated problem..:confused:

---

### Post by themusicalduck on 2009-01-11
I tried sudo tune2fs -U random /dev/sdc1 again while under my normal install and it worked, edited the fstab to use the new UUID as home like you suggested and it worked!

Thanks for all the help with it! My grub menu is still playing up a little but I can make a new thread for it if I can't fix it.

Thanks again.

---

### Post by logos34 on 2009-01-11
> **themusicalduck said:**
> I tried sudo tune2fs -U random /dev/sdc1 again while under my normal install and it worked, edited the fstab to use the new UUID as home like you suggested and it worked!

Thanks for all the help with it! My grub menu is still playing up a little but I can make a new thread for it if I can't fix it.

glad to help.  

For windows boot entry, try this:
> 
title Windows 7
root=UUID=28522AF05E631137
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

or 

> title Windows 7
root (hd2,1)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

