---
title: "Partition access"
date: 2006-03-12
forum: Desktop Environments
---

### Post by terranz on 2006-03-12
I've just installed 5.10 and I have a problem.
No write access to my windows partitions.
They are fat32 and they are mounted.  I followed online instrautions to enable root and root login but when I tried to change permissions, the tick boxes reverted to their previous state and trying to change ownership didn't work either.

Thanks in advance for any help.

---

### Post by alamba on 2006-03-12
Post your /etc/fstab file. 

A

---

### Post by terranz on 2006-03-12
Will do as soon as I'm home

---

### Post by Sutekh on 2006-03-12
[QUOTE=terranz]I've just installed 5.10 and I have a problem.
No write access to my windows partitions.
They are fat32 and they are mounted.  I followed online instrautions to enable root and root login but when I tried to change permissions, the tick boxes reverted to their previous state and trying to change ownership didn't work either.

Thanks in advance for any help.[/QUOTE]
You can't change ownership of a FAT32 partition, they don't support Linux ownership/permissions.

Also there is no need to enable root to gain access to those partitions.


Here's how you can.  You need to open a **Terminal** window and  edit your **/etc/fstab**.  

You should create a backup of the fstab before editing it
```
sudo cp /etc/fstab /etc/fstab_backup
```
Then you can edit it using 
```
sudo nano /etc/fstab
```
Once you have opened the fstab then you need modify the lines for mounting the FAT32 partitions.  
For a FAT32 partition you probably have a line like this one
```
/dev/hda1 /media/hda1 vfat defaults 0 0
```
You should change it to this one
```
[COLOR="Blue"]/dev/hda1[/COLOR]    [COLOR="Red"]/media/windows[/COLOR]   [COLOR="Green"]vfat[/COLOR]   [COLOR="DarkOrchid"]iocharset=utf8,umask=0000[/COLOR]   0   0
```
 - [COLOR="Blue"]/dev/hda1[/COLOR] - is the location of the FAT32 partition

 - [COLOR="Red"]/media/windows[/COLOR] - this is the folder where the partition will be mounted.  If this folder doesn't exist you will need to create it yourself ```
sudo mkdir [COLOR="Red"]/media/windows[/COLOR]
```
**Note** you don't have to use [COLOR="Red"]/media/windows[/COLOR], in my system I use [COLOR="Red"]/mnt/os-shared[/COLOR], its up to you

 - [COLOR="Green"]vfat[/COLOR] - this specifies the filesystem as fat

 - [COLOR="DarkOrchid"]iocharset=utf8,umask=0000[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  [COLOR="DarkOrchid"]umask=0000[/COLOR] allows read, write and execute access to the partition.

Once you've modified the /etc/fstab, you can save it (Ctrl+X), exit (Ctrl+O) and issue the command```
sudo mount -a
```This re-mounts the partitions, without you having to restart your computer.

Then you should be away

---

### Post by terranz on 2006-03-12
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       /home           ext3    defaults        0       2
/dev/hdb1       /media/documents vfat    defaults        0       0
/dev/hda5       /media/dump     vfat    defaults        0       0
/dev/hda8       /media/dvdrip   vfat    defaults        0       0
/dev/hda6       /media/games    vfat    defaults        0       0
/dev/hdb8       /media/swap20   vfat    defaults        0       0
/dev/hda9       /media/swap40   vfat    defaults        0       0
/dev/hdb7       /media/wintemp  vfat    defaults        0       0
/dev/hda1       /windows        ntfs    defaults        0       0
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by terranz on 2006-03-12
[QUOTE=Sutekh] - iocharset=utf8,umask=0000 - these options set the character encoding to utf8 (for special chars) and sets the umask. umask=0000 allows read, write and execute access to the partition.[/QUOTE]

Thanks I'll try that

---

### Post by Sutekh on 2006-03-12
[QUOTE=terranz]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       /home           ext3    defaults        0       2
/dev/hdb1       /media/documents vfat    defaults        0       0
/dev/hda5       /media/dump     vfat    defaults        0       0
/dev/hda8       /media/dvdrip   vfat    defaults        0       0
/dev/hda6       /media/games    vfat    defaults        0       0
/dev/hdb8       /media/swap20   vfat    defaults        0       0
/dev/hda9       /media/swap40   vfat    defaults        0       0
/dev/hdb7       /media/wintemp  vfat    defaults        0       0
/dev/hda1       /windows        ntfs    defaults        0       0
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0[/QUOTE]

Try a fstab like this
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       /home           ext3    defaults        0       2
/dev/hdb1       /media/documents vfat   **iocharset=utf8,umask=0000**    0       0
/dev/hda5       /media/dump     vfat    **iocharset=utf8,umask=0000**    0       0
/dev/hda8       /media/dvdrip   vfat    **iocharset=utf8,umask=0000**    0       0
/dev/hda6       /media/games    vfat    **iocharset=utf8,umask=0000**    0       0
/dev/hdb8       /media/swap20   vfat    **iocharset=utf8,umask=0000**    0       0
/dev/hda9       /media/swap40   vfat    **iocharset=utf8,umask=0000**    0       0
/dev/hdb7       /media/wintemp  vfat    **iocharset=utf8,umask=0000**    0       0
/dev/hda1       /windows        ntfs    **nls=utf8,umask=0222**          0       0
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
```

For the NTFS use umask=0222,this doesn't allow write access, which is not recommende for use in Linux.  Use
```
sudo mount -a
```after editing too.

---

### Post by terranz on 2006-03-12
I will try that, thanks.
I'll have to wait a while as I posted before from home during my lunch break and I'm back at work (1:42 in the afternoon)

---

### Post by terranz on 2006-03-13
> sudo mount -a

Didn't work so I had to restart but everything else did.  Thanks

---

### Post by Sutekh on 2006-03-13
[QUOTE=terranz]Didn't work so I had to restart but everything else did.  Thanks[/QUOTE]
It really should.  Did you recieve an error when you tried that command?

---

### Post by terranz on 2006-03-13
nope no error just a permissions error when I tested write access.

---

### Post by n8bounds on 2006-03-26
THANKS Sutekh, That was clear and super easy directions on how to fix exactly the problem I was having!  Thanks a lot!!!

---

### Post by n8bounds on 2006-03-26
OH, I can probably help--I noticed that when you use the "Disks" administration tool, try to mount a VFAT partition, THEN (when you figure out that you can only write to it as SU) go read the Ubuntu Forums and follow Sutekh's most gracious advice, that you have to DISABLE the partition from the Disks tool and then run the "sudo mount -a" cmd again...otherwise, you could just restart for the same effect.

---

