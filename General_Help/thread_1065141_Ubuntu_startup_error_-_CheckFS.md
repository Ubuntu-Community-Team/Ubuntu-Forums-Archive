---
title: "Ubuntu startup error - CheckFS"
date: 2009-02-09
forum: General Help
---

### Post by mCion on 2009-02-09
Hi.

I get an error while booting.  It is almost the same problem as this thread
[http://ubuntuforums.org/showthread.php?t=1026480&highlight=checkfs](http://ubuntuforums.org/showthread.php?t=1026480&highlight=checkfs)
exept that the line is correct.  

I think this might have to do with that I eliminated a partition and merged it with another one

please see 
---checkfs---
Log of fsck -C3 -R -A -a 
Mon Feb  9 14:30:56 2009

fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Unable to resolve 'UUID=11312c51-94fa-43e9-a05b-ccba8c78836f'

fsck died with exit status 8

Mon Feb  9 14:30:56 2009
----------------

and  this is what I get when I type: sudo blkid

/dev/sda1: UUID="88B8A40BB8A3F63A" LABEL="TOSHIBA SYSTEM VOLUME" TYPE="ntfs" 
/dev/sda2: UUID="F40AAAEB0AAAAA56" LABEL="SQ004434V02" TYPE="ntfs" 
/dev/sda3: UUID="11312c51-94fa-43e9-a05b-ccba8c78836f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="46a22020-917b-4273-a44c-14529093ba21" 
/dev/sda6: UUID="0af759cc-1456-4e72-a311-bffb85fcff38" SEC_TYPE="ext2" TYPE="ext3" 

-----

this is fstab---

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0af759cc-1456-4e72-a311-bffb85fcff38 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
UUID=88B8A40BB8A3F63A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=F40AAAEB0AAAAA56 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=11312c51-94fa-43e9-a05b-ccba8c78836f /media/sda3     ext3    defaults,relatime        0       2
# /dev/sda5
UUID=46a22020-917b-4273-a44c-14529093ba21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

------

In GParted I see that I only have drives sda1, sda2, sda4 (which is subdivided with my main ubuntu drive and a swap)

any help?

should I change the FSTAB from sda3 to sda4??

thank you!

---

### Post by adder1972 on 2009-02-09
Hi,

From the info you are posting, it doesn't seem that the UUIDs have changed.

Try to comment out this line in your fstab:

UUID=11312c51-94fa-43e9-a05b-ccba8c78836f /media/sda3 ext3 defaults,relatime 0 2

(Use gksudo gedit /etc/fstab and put a '#' in front of the line).

Reboot and see what happens.

---

### Post by mCion on 2009-02-09
Perfect Adder1972!!, Thanks!!

---

