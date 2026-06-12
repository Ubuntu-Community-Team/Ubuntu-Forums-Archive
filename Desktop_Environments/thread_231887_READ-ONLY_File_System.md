---
title: "READ-ONLY File System"
date: 2006-08-07
forum: Desktop Environments
---

### Post by dolphin_1 on 2006-08-07
Having a little trouble here.

During install, I made a seperate nfts partition which I mounted as /files so as to hold my files in a seperate part of the hard drive.  The /files directory is present but I cannot write to it.

/etc/fstab originally looked like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /files          ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


Then I changed the sda6 line to look like this:
```
/dev/sda6       /files          ntfs    rw        0       1
```
thinking I could force it to read/write.

reboot machine, but no luck.

Then did:              chmod u+w /files
and got this response: READ-ONLY file system

Another clue:  sda6 in the GNOME device manager has this detail:
```
volume.mount.valid_options    list  ro,sync,dirsync,noatime,nodiratime,noexec,quiet
```

Where did I go wrong ?

---

### Post by simonn on 2006-08-07
ntfs is read only under linux.

There is a user space tool (meaning a utility as opposed to a driver in the kernel) which can write to ntfs apparently, but I cannot remember what it is called (windows free home... :)).

---

### Post by darkshadow on 2006-08-08
I think you need ntfs-3g to write to a ntfs partition but I may be wrong as I am windows free in my home.
Also if that partition is just for files and I noticed no other partition that could have windows why even have a windows filesystem instead of a Linux one.
My suggestion if you need it so windows can read it just format it as fat32 which is supported by Linux.

---

### Post by JasonValdron on 2006-08-08
I already tried to run one, can't remember the name, it was something ntfs lol Well the problem is that it WAS working fine, until the day that it made my computer freaked out, the hard drive crashed, had to send it back. If you need file sharing between a dual-boot windows/linux, go with fat32 OR ext2, you can get a driver for windows for reading ext2 ONLY not ext3, it will work but crash after a while.

---

### Post by RAOF on 2006-08-08
> **JasonValdron said:**
> ...
 go with fat32 OR ext2, you can get a driver for windows for reading ext2 ONLY not ext3, it will work but crash after a while.
That driver is from [fs-driver.org](fs-driver.org), and reads/writes to EXT3 just fine.  It doesn't update the journal on an EXT3 filesystem, but that's ok.

From the site:
> 
Does the Ext2 driver access Ext3 volumes, too?

The Ext3 file system is the Ext2 file system which has been extended by journaling. Ext3 is backward-compatible to Ext2 - an Ext3 volume can be mounted and used as an Ext2 volume. Just as older Linux Kernels which do not know the Ext3 file system can mount Ext3 volumes (as Ext2 volumes), the Ext2 file system driver ext2fs.sys for Windows incorporated in this software package can do it without any problems, too. Of course you do not take advantage of the journaling of the Ext3 file system if you mount it as an Ext2 file system.

Journaling keeps the file system of a volume consistent, even though the volume has not been cleanly dismounted in the past (for instance because the computer has crashed): There is no need for running e2fsck (the "chkdsk" of the Ext2/Ext3 file system on Linux).


---

### Post by dolphin_1 on 2006-08-08
Good advice,  but something else went wrong.   read on.....

I did what you suggested and reformatted the ntfs partition to a fat32,
then changed the 'fstab' file to match, then gave permissions using chmod and all was well.  I could finally write to it.  I wanted to move files from one machine to another so ..

I set up NFS server '/etc/exports' file on this pc as follows:
```
/files		jellyfish(rw,sync)
```

and did a 
```
mount dolphin:/files /mnt/private2
```
on my older Debian machine

The problem is that the /files folder is apparently on the same partition as the Ubuntu operating system.  I discovered this when an error came up saying my sda2 partition is full.  And sure enough it is.  I checked it with Gparted.  The data I moved over should have been going into the FAT32 partition.

The fstab file says I've mounted sda6 as /files but in reality sda6 is still empty after supposedly moving 5 GB to it.

Have you ever seen this before?

---

