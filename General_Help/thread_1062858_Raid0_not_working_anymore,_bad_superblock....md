---
title: "Raid0 not working anymore, bad superblock..."
date: 2009-02-07
forum: General Help
---

### Post by cam217 on 2009-02-07
Hi,

I changed to ubuntu-studio intrepid 64 bits from another ubuntu so I kept my /home and other partitions on another disks include a raid0 array called janbeuhnoix. Since last installation my md0 array seems to have issues. It dosen't work anymore.

Here is what I have:
```
cam@intrepid-studio:~$ sudo fdisk -l

Disk /dev/sda: 74.0 GB, 74000000000 bytes
255 heads, 63 sectors/track, 8996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00029ad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         486     3903763+  82  Linux swap / Solaris
/dev/sda2   *         487        2918    19535040   83  Linux
/dev/sda3            2919        8996    48821535   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3f33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sdb2            6528       30401   191767905   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003286b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641   fd  Linux raid autodetect

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19e219e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   fd  Linux raid autodetect

```

```
cam@intrepid-studio:/proc$ sudo mdadm --misc -E /dev/sdc1 /dev/sdd1 /dev/md0
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : edf2cdd8:ded5032d:33a70373:7f0eea01
  Creation Time : Sat Apr 14 05:01:06 2007
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sat Apr 14 05:28:16 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b4ea9ca7 - correct
         Events : 5

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : edf2cdd8:ded5032d:33a70373:7f0eea01
  Creation Time : Sat Apr 14 05:01:06 2007
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sat Apr 14 05:28:16 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : b4ea9c95 - correct
         Events : 5

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
mdadm: No md superblock detected on /dev/md0.

```

```
cam@intrepid-studio:~$ more /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 devices=/dev/sdc1,/dev/sdd1 level=raid0 num-devices=2 UUID=edf2cdd8:ded5032d:33a70373:7f0eea01

# This file was auto-generated on Sun, 01 Feb 2009 19:56:56 +0000
# by mkconf $Id$
```

```
cam@intrepid-studio:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5a64b7a0-53a6-476d-8e95-bed15a5e7ead /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=1a3ad476-bea7-4d30-914c-25d074623643 /home           ext3    relatime        0       2
# /dev/md0
UUID=edf2cdd8:ded5032d:33a70373:7f0eea01 /media/janbeuhnoix ext3    relatime        0       2
# /dev/sdb2
UUID=999abaab-40ef-40a0-9fc1-977eff5f13a2 /media/share    ext3    relatime        0       2
# /dev/sdb1
UUID=10E0D6E7E0D6D1D8 	/media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=dd1c5856-ad2e-42b6-a08d-2406b68fe6d6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

```
cam@intrepid-studio:~$ more /proc/partitions 
major minor  #blocks  name

   8     0   72265625 sda
   8     1    3903763 sda1
   8     2   19535040 sda2
   8     3   48821535 sda3
   8    16  244198584 sdb
   8    17   52428096 sdb1
   8    18  191767905 sdb2
   8    32  312571224 sdc
   8    33  312568641 sdc1
   8    48  312571224 sdd
   8    49  312568641 sdd1
 254     0  625137920 dm-0
 254     2  312568641 dm-2

```

All seems to be correct to me but mount don't work.
```
cam@intrepid-studio:~$ sudo mdadm --assemble /dev/md0 /dev/sd[cd]1
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has no superblock - assembly aborted
```

I tried
```
cam@intrepid-studio:~$ sudo mdadm --create /dev/md0 --assume-clean --level=0 --raid-devices=2 /dev/sdc1 /dev/sdd1
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: create aborted
```

It's strange that sdc1 and sdd1 doesn't appear in this command but in next one...
```
cam@intrepid-studio:~$ sudo /bin/ls -lF /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 10E0D6E7E0D6D1D8 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 1a3ad476-bea7-4d30-914c-25d074623643 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 5a64b7a0-53a6-476d-8e95-bed15a5e7ead -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 999abaab-40ef-40a0-9fc1-977eff5f13a2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 dd1c5856-ad2e-42b6-a08d-2406b68fe6d6 -> ../../sda1
```
```
cam@intrepid-studio:~$ sudo /bin/ls -lF /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 2009-02-07 11:16 ata-MAXTOR_STM3250310AS_9RY19XRQ -> ../../sdb
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 ata-MAXTOR_STM3250310AS_9RY19XRQ-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 ata-MAXTOR_STM3250310AS_9RY19XRQ-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 2009-02-07 11:16 ata-SAMSUNG_HD321KJ_S0MQJ1KP101021 -> ../../sdc
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 ata-SAMSUNG_HD321KJ_S0MQJ1KP101021-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2009-02-07 11:16 ata-SAMSUNG_HD321KJ_S0MQJ1KP101256 -> ../../sdd
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 ata-SAMSUNG_HD321KJ_S0MQJ1KP101256-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 2009-02-07 11:16 ata-WDC_WD740GD-75FLA0_WD-WMAKE1089813 -> ../../sda
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 ata-WDC_WD740GD-75FLA0_WD-WMAKE1089813-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 ata-WDC_WD740GD-75FLA0_WD-WMAKE1089813-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 ata-WDC_WD740GD-75FLA0_WD-WMAKE1089813-part3 -> ../../sda3
lrwxrwxrwx 1 root root 39 2009-02-07 11:16 dm-name-isw_bdcciigdbc_Janbeuhnoix -> ../../mapper/isw_bdcciigdbc_Janbeuhnoix
lrwxrwxrwx 1 root root 40 2009-02-07 11:16 dm-name-isw_bdcciigdbc_Janbeuhnoix1 -> ../../mapper/isw_bdcciigdbc_Janbeuhnoix1
lrwxrwxrwx 1 root root 39 2009-02-07 11:16 dm-uuid-DMRAID-isw_bdcciigdbc_Janbeuhnoix -> ../../mapper/isw_bdcciigdbc_Janbeuhnoix
lrwxrwxrwx 1 root root 40 2009-02-07 11:16 dm-uuid-DMRAID-isw_bdcciigdbc_Janbeuhnoix1 -> ../../mapper/isw_bdcciigdbc_Janbeuhnoix1
lrwxrwxrwx 1 root root  9 2009-02-07 11:16 scsi-1ATA_MAXTOR_STM3250310AS_9RY19XRQ -> ../../sdb
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 scsi-1ATA_MAXTOR_STM3250310AS_9RY19XRQ-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 scsi-1ATA_MAXTOR_STM3250310AS_9RY19XRQ-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 2009-02-07 11:16 scsi-1ATA_SAMSUNG_HD321KJ_S0MQJ1KP101021 -> ../../sdc
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 scsi-1ATA_SAMSUNG_HD321KJ_S0MQJ1KP101021-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2009-02-07 11:16 scsi-1ATA_SAMSUNG_HD321KJ_S0MQJ1KP101256 -> ../../sdd
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 scsi-1ATA_SAMSUNG_HD321KJ_S0MQJ1KP101256-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 2009-02-07 11:16 scsi-1ATA_WDC_WD740GD-75FLA0_WD-WMAKE1089813 -> ../../sda
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 scsi-1ATA_WDC_WD740GD-75FLA0_WD-WMAKE1089813-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 scsi-1ATA_WDC_WD740GD-75FLA0_WD-WMAKE1089813-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-02-07 11:16 scsi-1ATA_WDC_WD740GD-75FLA0_WD-WMAKE1089813-part3 -> ../../sda3
```

I don't why but in last I can see both samsung disks works great but I can't use it. Isn't that strange in "mdadm -E" command that I ask for sdc1 sdd1, I get informations on sdc1 and sdb1... what you think I should do with this raid (I hope I can get back all my datas)
If anyone have an idea about what I should do then let me know plz.

---

### Post by fjgaude on 2009-02-07
For starters the UUID of the drives of your array, /dev/md0, is not what you use to mount the array. Notice that the same UUID is for both drives. That's how **mdadm** knows the drives are of the same array.

You mount with just using the /dev/md0 as the array name. Or you can find the array UUID using:

```
sudo blkid /dev/md0
```

and use that but it is not necessary.

Let us know how you are doing.

---

### Post by cam217 on 2009-02-07
This command doesn't gave me any output. Like I wrote, "more /proc/mdstat" give me empty output too.

EDIT: I tried using /dev/sdXX instead of UUID in fstab but it doesn't change anything.

---

### Post by fjgaude on 2009-02-08
I would guess that /dev/md0 doesn't exist, not assembled or mounted. Use the name in your fstab file instead of that UUID that is there.

---

### Post by cam217 on 2009-02-08
I saved this /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
/dev/sda2	/               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
/dev/sda3	/home           ext3    relatime        0       2
# /dev/md0
/dev/md0 	/media/janbeuhnoix ext3    relatime        0       2
# /dev/sdb2
/dev/sdb2	/media/share    ext3    relatime        0       2
# /dev/sdb1
/dev/sdb1 	/media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
/dev/sda1	none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

It seems that didn't solve the problem at all.

---

### Post by fjgaude on 2009-02-08
Okay, move the md0 line to be the last one in fstab:

```
# /dev/md0
/dev/md0     /media/janbeuhnoix ext3    relatime    0     2
```

Reboot... if that doesn't work, then do this:

```
sudo mdadm --assemble /dev/sdc1 /dev/sdd1
```

and see how that goes.

---

### Post by cam217 on 2009-02-09
Hi,

Moving md0 line at the bottom of the /etc/fstab didn't change anything and as I wrote you in my first message, assemble doesn't work:

[QUOTE="cam217"]```
cam@intrepid-studio:~$ sudo mdadm --assemble /dev/md0 /dev/sd[cd]1
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has no superblock - assembly aborted
```[/QUOTE]

---

### Post by cam217 on 2009-02-09
If we take a look at the "*more /proc/partitions*" we can see that:
sdc1 is major=8 and minor=33
sdb1 is major=8 and minor=17

just the same we can see at the end of the superblock --> "*mdadm --misc -E /dev/sdc1 /dev/sdd1*"

I think I just have to change "*sdb1 major=8 minor=17*" to "*sdd1 major=8 minor=49*" but I don't how I can do this.

Does anyone have any idea of what I have to do in this case? Thanks

---

### Post by djamu on 2009-02-09
still have problems ?
was a couple days out ...

mdadm.conf tries to assemble the correct disks 

> 
ARRAY /dev/md0 devices=/dev/sdc1,/dev/sdd1 level=raid0 num-devices=2 
UUID=edf2cdd8:ded5032d:33a70373:7f0eea01


but 

> 
cam@intrepid-studio:/proc$ sudo mdadm --misc -E [COLOR="Red"]/dev/sdc1[/COLOR] [COLOR="Red"]/dev/sdd1[/COLOR] /dev/md0
/dev/sdc1:
....snipsnip...
  UUID : edf2cdd8:ded5032d:33a70373:7f0eea01
....snipsnip....
       Checksum : b4ea9ca7 - correct
       Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   [COLOR="Red"]/dev/sdc1[/COLOR]

   0     0       8       17        0      active sync   [COLOR="Red"]**_/dev/sdb1_**[/COLOR]
   1     1       8       33        1      active sync   [COLOR="Red"]/dev/sdc1[/COLOR]


uses wrong disks ... because of wrong UUID's on individual devices ( possible recent reformat of /dev/sdb ? > a new dualboot windows install ? )

show me > mdadm -E /dev/sdb 
and mdadm -E /dev/sdb1

and then
remove /etc/mdadm.conf and reboot 
try to do a manual assemble of md0 > with /dev/sdc1 /dev/sdd1 ...

if this works ....

both the physical devices and the MD devices have their own "superblocks" ... most likely you need to wipe/rewrite the MD superblocks and let mdadm create a new mdadm.conf file > don't worry it doesn't affect the filesystem on the volume ...

then PM me

if this doesn't work 

PM me,  it will be a bit harder :roll:




I

---

### Post by cam217 on 2009-02-10
Thanks for your reply Djamu ;)

I'll try this as soon as I get back home (i'm currently at work :P)
I'll PM you if your suggestion doesn't work. For info, the only partition which was reformated is /dev/sda1 (swap)

---

### Post by cam217 on 2009-02-10
Hi again,

I tried exactly what u told me but it didn't work, I still have :
```
sudo mdadm --assemble /dev/md0 /dev/sd[cd]1
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has no superblock - assembly aborted
```

It seems that there's no superblock for the /dev/sdb1
```
cam@intrepid-studio:~$ sudo mdadm -E /dev/sdb 
mdadm: No md superblock detected on /dev/sdb.
cam@intrepid-studio:~$ sudo mdadm -E /dev/sdb1
mdadm: No md superblock detected on /dev/sdb1.
```
 
I'm waiting for your reply then, let's get dirty hands :lolflag:

---

### Post by fjgaude on 2009-02-10
Wow, after going over data you posted I think that you should try something that usually works... no risk involed. Your **mdadm.conf** file is not standard and should not have the drive names in it along with the UUID of the array, which is the same as the UUID of each drive in the array.

Please do this: re-name or delete the mdadm.conf file, remove **mdadm** using apt-get, reboot. Then re-install mdadm and run this command:

```
sudo mdadm --assemble --scan
```

A new auto-created mdadm.conf file will have been created and you should be good to.

Let us know how you are doing.

---

### Post by djamu on 2009-02-10
> **fjgaude]
Please do this: re-name or delete the mdadm.conf file, remove mdadm using apt-get, reboot. Then re-install mdadm and run this command:
[/QUOTE]
second that ... might be a borked mdadm install ...
even better is it to completely purge the mdadm installation prior to reinstalling it ...
```

sudo apt-get purge mdadm
reboot

```


if that doesn't fix it ... bear with me ...




[QUOTE=cam217 said:**
> Hi again,

I tried exactly what u told me but it didn't work, I still have :
I'm waiting for your reply then, let's get dirty hands :lolflag:

k, before you actually do something ...

did you delete /etc/mdadm/mdadm.conf    prior to a reboot ?

if not do exactly following...
remove ( comment out ) any ( md) raid mounts in /etc/fstab  > make sure none mounts
remove /etc/mdadm/mdadm.conf

reboot

after reboot give me following output

```
sudo cat /proc/mdstat
```

**no MD devices did start ... **

Now you should be able to manually assemble ( include rewrite superblocks > see my other posts on this topic )  ...

Since this is a 2disks striped array ... there's 2 ways to assemble it ... if 1 assemble fails to mount the filesystem > reassemble it the way around( switch the physical devices) and try to remount > ... this should work ..
(and don't use the missing statement ... this is only for redundant arrays ... )


**any MD device did start ... **

despite the absense of a config-----

Quite normal.. the mdadm daemon doesn't really need /etc/mdadm/mdadm.conf and may assemble any array that has valid superblocks ....
Leftover superblocks may cause a system to recognize multiple valid raid arrays on a fixed set of disks, only 1(*) of  those arrays has a valid / recognizable FS....

(*) in rare cases your system may recognize a ( obviously ) severely damaged FS from a long gone installation .... so never ever ever........ ever .... use fsck on a volume from which you are not confident it's the right one ....
( work read - only )
same goes for reassembling redundant arrays ( raid4/ 5 / 6 )  always use the **missing** statement ( 2  for raid6 ) when manually reassembling arrays > preventing the array from rebuilding redundancy > and overwriting data on a wrong assembled one




let me hear what's up

---

### Post by fjgaude on 2009-02-10
Thanks, djamu, for coming to aid. You are of ubuntu:

A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed. -- Archbishop Desmond Tutu, 1999

---

### Post by cam217 on 2009-02-11
Hi,

Yes Djamu, I did remove mdadm.conf and restart but I didn't comment out md lines in fstab. I'll try this before going further.

I'll try this all tonight because I'm currently at work and I'll keep you posted, thanks to both of you trying to help me ;)

---

### Post by cam217 on 2009-02-11
So,

After uninstall mdadm with purge option, I commented md0 line in /etc/fstab and reboot. Here is my mdstat:

```
cam@intrepid-studio:~$ sudo more /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>

```

At this point, I should be able to assemble md0 but it didn't work better
```
cam@intrepid-studio:~$ sudo mdadm --assemble /dev/md0 /dev/sd[cd]1
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has no superblock - assembly aborted
```
I tried to create it too but it wasn't better
```
cam@intrepid-studio:~$ sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sd[cd]1
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: create aborted

```

---

### Post by fjgaude on 2009-02-11
What does your mdadm.conf file look like now?

I feel you haven't followed our advise exactly as stated. <smile>

Try doing an assembly without the drive names:

```
sudo mdadm --assemble --scan
```

---

### Post by cam217 on 2009-02-11
Doesn't  work either

```
cam@intrepid-studio:~$ sudo mdadm --assemble --scan
[sudo] password for cam: 
mdadm: no devices found for /dev/md0

```

---

### Post by fjgaude on 2009-02-11
I'm lost, don't have any suggestions as to how to fix your issue. Maybe someone else here has an idea.

---

### Post by cam217 on 2009-02-12
I hope so :)

---

### Post by djamu on 2009-02-12
oops missed a bunch of replies ...

it's strange it gives ```
Device or resource busy
``` errors

you sure you haven't mounted anything related ?
you mind that I take a look over an ssh session (PM)?

---

### Post by cam217 on 2009-02-12
Hi,

I'm pretty sure that sdc1 and sdd1 aren't mounted anywhere so I wonder why i get this error. I can let you take a look via ssh but tomorrow I'm going snowboarding until next tuesday. :mrgreen: We'll take a look next week ;)
Thanks for your help.

---

### Post by djamu on 2009-02-12
oow snowboarding ... where ? ( I'm from belgium )

---

### Post by cam217 on 2009-02-12
I'm french and I went to Chatel for the new year and now i'm going to barèges-La Mongie. I took a long week-end at work. :D

---

### Post by cam217 on 2009-02-21
Finally it seems to be a corrupt install because the raid array worked on a live CD but still out of order on my installed disto. I'll test a new install and keep posted ;)

---

### Post by cam217 on 2009-02-21
Works fine now on ubuntu jaunty 9.04 alpha with ext4 on / :p

---

### Post by cam217 on 2009-02-23
After update, mdadm did update and then I've got back the same problem. It seems that actual version of jaunty jackalope alpha4 have a bugged mdadm. I'll go back to intrepid ibex until stable jaunty jackalope release.

---

