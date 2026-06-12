---
title: "How to write into Windows partition and modify the files???"
date: 2005-12-14
forum: Desktop Environments
---

### Post by rockusnarus on 2005-12-14
It is nice that Ubuntu automounts the Windows Drives. But I am not able to modify the files or write into those partitions even after I enter into the administrative mode by entering my password (I am the only user). I could easily do that Red Hat and Knoppix which I used before (I think so, but it was a long time ago so I may be wrong :???:). Can somebody help me with this issue? It is very important for my work and without this I am severely handicapped.:(
I use Windows XP Professional and Breezy.

---

### Post by tlc on 2005-12-14
Your windows partitions are probably mounted read-only in /etc/fstab. Please post that file and I can tell you what to change there. Basically if it says 'ro' on the appropriate line just change it to 'rw' IIRC.

---

### Post by art on 2005-12-14
There is a project called Captive NTFS, which let's you write on NTFS. But I think people say you might screw up your Windows partition. So be carefull.

---

### Post by rockusnarus on 2005-12-14
Thanx for your prompt help! Let me try modifying the fstab file. If I am not successful I'll post the fstab contents.:)

---

### Post by rockusnarus on 2005-12-14
Well, I can't really decode the fstab. I am posting it here. 
[php] # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda7       /media/hda7     vfat    defaults        0       0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hda9       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/php]

---

### Post by gosh on 2005-12-14
Linux does not support NTFS, the filesystem XP uses.

I partition my disk as follows:
- small NTFS for XP system files
- bigger part for Ubuntu
- big FTS32 partition for my documents, music etc which I can read/write in XP and Ubuntu.

---

### Post by healychan on 2005-12-14
[QUOTE=gosh]Linux does not support NTFS, the filesystem XP uses.

I partition my disk as follows:
- small NTFS for XP system files
- bigger part for Ubuntu
- big FTS32 partition for my documents, music etc which I can read/write in XP and Ubuntu.[/QUOTE]


This is not true. Some new Linux(ubuntu as well) does support NTFS, but read only.:razz:

---

### Post by gosh on 2005-12-14
[QUOTE=healychan]This is not true. Some new Linux(ubuntu as well) does support NTFS, but read only.:razz:[/QUOTE]

Yes, of course you're right. Sorry for the misunderstanding:oops:

---

### Post by briancurtin on 2005-12-14
[QUOTE=healychan]This is not true. Some new Linux(ubuntu as well) does support NTFS, but read only.:razz:[/QUOTE]
its not really a new thing; and as far as the original poster is concerned, NTFS write access isnt supported, so its not supported as a whole to him.

if write access to a drive shared by windows is very important to you, id dump NTFS. as pointed out earlier, there is/are project(s) out there working on NTFS writing, but if it is as important as you make it seem i would look into FAT based formats to get to it from *nix and windows.

---

### Post by rockusnarus on 2005-12-14
Leave the NTFS partition! I can't even access the vfat ones. Please help!

---

### Post by Mazaev on 2005-12-14
[QUOTE=rockusnarus]Well, I can't really decode the fstab. I am posting it here. 
[php] # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda7       /media/hda7     vfat    defaults        0       0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hda9       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/php][/QUOTE]
Change the "defaults" under "options" field on your Windows drives to this:

```

owner,uid=1000,gid=100,async,rw 0 0

```

---

### Post by rockusnarus on 2005-12-14
Thanks a lot.it is working fine Now!:D

---

### Post by Puck7 on 2008-04-14
Hi. 

I have the same problem. Can you help me change my fstab too pleasE ? 

Here is what i found in the file :
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e4840df2-75ac-4009-8d0e-119afe993682 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=24C431C3C431984E /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=58F4226DF4224E16 /media/sda4     ntfs    owner,uid=1000,gid=100,async,rw 0 0
# /dev/sda2
UUID=3a93c0aa-aa16-42c5-aba5-2b1c70c7978e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
[/PHP]

I already changed the defaults under options for the sda4, because that`s the partition i want too write too from ubuntu, but it still sais i don`t have permission to do so. Can you help me out please ? Thank you.

---

