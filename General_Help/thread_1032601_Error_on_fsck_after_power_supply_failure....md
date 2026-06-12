---
title: "Error on fsck after power supply failure..."
date: 2009-01-06
forum: General Help
---

### Post by Ifaistos on 2009-01-06
Very recently the power supply of my rig got blown up.  After I replaced it, I get an error when Ubuntu starts up and the boot up process stops.
It's no big deal, because I type "exit" and the boot up process continues.

However I would like to find out what this is all about.
When the boot-up process stops, I get a message saying that the details of the problem are stored in the file in /var/log/fsck/checkfs

Below are the contents of the file.
Does anyone know what has happened, and how to fix this?

Thank you all :)

----------------------------------------------------------------
Log of fsck -C3 -R -A -a 
Tue Jan  6 21:24:57 2009

fsck 1.41.3 (12-Oct-2008)
/dev/sda2: clean, 27653/22839296 files, 11166756/45654721 blocks
Failed to open the device 'UUID=c9ae54a0-69e0-4939-9960-24347efb0eb5': No such file or directory


fsck died with exit status 8

Tue Jan  6 21:24:58 2009
----------------

---

### Post by Herman on 2009-01-06
You should run the command 'blkid', or if that doesn't work, try 'sudo blkid'. You should be given a list of all your partitions with their file system UUID numbers.
```
sudo blkid

```Copy that list, and then open /etc/fstab, 
```
gksudo gedit /etc/fstab
```You can (temporarily) paste your list of UUID numbers to the bottom of your /etc/fstab file while you check to see if your current UUID numbers, (from the list), match your UUID numbers you had in /etc/fstab.

Sometimes, especially after you have done some work with a partition editor and re-formatted a partition/ added a new partition, etc, your file system UUID numbers in /etc/fstab need to be manually updated.
You will probably see a UUID number in your /etc/fstab that's out of date, just copy the current one from the matching partition in your blkid list and paste that number over the old number in /etc/fstab to overwrite it. That will correct your /etc/fstab file, which is the file that controls which file systems will be checked and mounted automatically at each boot-up.

When you are finished, you can either delete the blkid output which you pasted there temporarily, or place hash marks before each line to 'comment it out', then you can leave it there for future reference, that's what I do.

Regards, Herman :D

---

### Post by Ifaistos on 2009-01-06
Found below is my fstab file and at the end, commented out is the output of the blkid command.
I couldn't find any difference between the UUIDs for sda2.
Is it just me? am I missing smt?

Thanks :-)



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=db222afc-9936-45c2-bb33-7807c8871c5e /               reiserfs notail,relatime 0       1
# /dev/sda2
UUID=c823defe-c2e5-4e64-aadb-074d75059ffc /home           ext3    relatime        0       2
# /dev/sdc1
UUID=c9ae54a0-69e0-4939-9960-24347efb0eb5 /media/sdc1     reiserfs relatime        0       2
# /dev/sdb1
UUID=EACCD32ECCD2F433 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=13fccc89-1c14-433b-b96c-239a759c3b61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# /dev/sda1: UUID="db222afc-9936-45c2-bb33-7807c8871c5e" TYPE="reiserfs" 
# /dev/sda2: UUID="c823defe-c2e5-4e64-aadb-074d75059ffc" TYPE="ext3" SEC_TYPE="ext2" 
# /dev/sda3: TYPE="swap" UUID="13fccc89-1c14-433b-b96c-239a759c3b61" 
# /dev/sdb1: UUID="EACCD32ECCD2F433" LABEL="400 GB" TYPE="ntfs" 
# /dev/sdc1: LABEL="Movie Editor" UUID="29f0dfc6-617a-4e9c-aa59-551a0b78e6d5" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by Herman on 2009-01-07
> I couldn't find any difference between the UUIDs for sda2.
Is it just me? am I missing smt?
 Your sda2 UUID numbers are okay. Your /sdc1 UUID number isn't though.
> Failed to open the device 'UUID=[COLOR=Red]**c9ae54a0-69e0-4939-9960-24347efb0eb5**[/COLOR]': No such file or directory```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=db222afc-9936-45c2-bb33-7807c8871c5e / reiserfs notail,relatime 0 1
# /dev/sda2
UUID=c823defe-c2e5-4e64-aadb-074d75059ffc /home ext3 relatime 0 2
[B]# /dev/sdc1
UUID=[COLOR=Red]c9ae54a0-69e0-4939-9960-24347efb0eb5[/COLOR] /media/sdc1 [COLOR=Red]reiserfs relatime[/COLOR] 0 [COLOR=Black]2[/COLOR][/B]
# /dev/sdb1
UUID=EACCD32ECCD2F433 /windows ntfs defaults,umask=007,gid=46 0 1
# /dev/sda3
UUID=13fccc89-1c14-433b-b96c-239a759c3b61 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

# /dev/sda1: UUID="db222afc-9936-45c2-bb33-7807c8871c5e" TYPE="reiserfs"
# /dev/sda2: UUID="c823defe-c2e5-4e64-aadb-074d75059ffc" TYPE="ext3" SEC_TYPE="ext2"
# /dev/sda3: TYPE="swap" UUID="13fccc89-1c14-433b-b96c-239a759c3b61"
# /dev/sdb1: UUID="EACCD32ECCD2F433" LABEL="400 GB" TYPE="ntfs"
# **/dev/sdc1: LABEL="Movie Editor" UUID="[COLOR=DarkGreen]29f0dfc6-617a-4e9c-aa59-551a0b78e6d5[/COLOR]" SEC_TYPE="[COLOR=DarkGreen]ext2[/COLOR]" TYPE="[COLOR=DarkGreen]ext3[/COLOR]"**
```It looks to me as if you or someone has reformatted /dev/sdc1. It used to have a reiser file system and now it has an ext file system whith the label "Movie Editor".
I think you should copy the number I highlighted here is green and paste it over the number in your /etc/fstab file which looks like the one I have highlighted in red. 

Regards, Herman :D

---

