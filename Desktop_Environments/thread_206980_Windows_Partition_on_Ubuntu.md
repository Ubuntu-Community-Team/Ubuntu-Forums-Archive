---
title: "Windows Partition on Ubuntu"
date: 2006-06-30
forum: Desktop Environments
---

### Post by thepocketdrummer on 2006-06-30
I was looking through the Ubuntu 6.06 Guide and I found instructions to access the windows partition from within Linux. I made the folder and did everything it asked, but I still cannot access the partition. It says I do not own it. Also, there is nothing in that file that it made me create. What can I do to get it working?  #-o

---

### Post by Buffalo Soldier on 2006-07-01
[QUOTE=thepocketdrummer]I was looking through the Ubuntu 6.06 Guide and I found instructions to access the windows partition from within Linux. I made the folder and did everything it asked, but I still cannot access the partition. It says I do not own it. Also, there is nothing in that file that it made me create. What can I do to get it working?  #-o[/QUOTE]
How about including more information? The content of your **/etc/fstab** files and the output from the command **sudo fdisk -l** would make it easier for others to help. Example:

1. Content of **/etc/fstab** file:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /media/winxp    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       /media/buffer   vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

2. Output from **sudo fdisk -l** command:
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        1397      979965    b  W95 FAT32
/dev/hda3            1398        1579     1461915   82  Linux swap / Solaris
/dev/hda4            1580        9729    65464875   83  Linux
```

---

### Post by thepocketdrummer on 2006-07-01
oh ok, I'll go ahead and post those when I get home... in an hour or so. (I work late)

Also, does anyone know a good place to learn the ins and outs of Ubuntu. I'm trying really hard to learn all that I can, but I get really confused how people know what to enter.

... oh, and is there a place to submit requests for things I'd like to see in linux?

---

### Post by randell6564 on 2006-07-01
[QUOTE=thepocketdrummer]oh ok, I'll go ahead and post those when I get home... in an hour or so. (I work late)

Also, does anyone know a good place to learn the ins and outs of Ubuntu. I'm trying really hard to learn all that I can, but I get really confused how people know what to enter.

... oh, and is there a place to submit requests for things I'd like to see in linux?[/QUOTE]

Go here [http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)  for pretty much all you need as a new ubuntu user.

And here [http://www.linuxquestions.org/questions/showthread.php?t=105955](http://www.linuxquestions.org/questions/showthread.php?t=105955)  for requesting things that you would like to see in Linux.

Have Fun!  :)

---

### Post by thepocketdrummer on 2006-07-01
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

```

That's the first one...

---

### Post by thepocketdrummer on 2006-07-01
And the second...

```
Disk /dev/hda: 80.0 GB, 80000040960 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/hda2            8925        9653     5855692+  83  Linux
/dev/hda3            9654        9726      586372+   5  Extended
/dev/hda5            9654        9726      586341   82  Linux swap / Solaris

```

---

### Post by Buffalo Soldier on 2006-07-01
My suggestions:[list]
[*] There are two lines refering to the same **/dev/hda1**. Try deleting or comment the first one.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
**[color=red]# /dev/hda1       /media/hda1     ntfs    defaults        0       0[/color]**
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**[color=blue]/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0[/color]**
```

[*] after editing the /etc/fstab file, remember to run command **sudo mount -a**

[/list]

---

### Post by thepocketdrummer on 2006-07-01
> Try deleting or comment the first one.

What do you mean by comment? What would happen if I just erased the first?

---

### Post by randell6564 on 2006-07-01
[QUOTE=thepocketdrummer]What do you mean by comment? What would happen if I just erased the first?[/QUOTE]

The little '#' is a comment. if you were to put that comment in front of the /dev/hda1 that buffalo soldier has shown in RED, then you will disable that line.

---

### Post by MrMojoRising on 2006-07-01
What he means by commenting is this.....

That text file is read by the mounting program 1 line at a time...... if the program sees a " # " as the first character in a line it ignores that line completely. It's the same idea as deleting it... but with commenting you can always revert back to your old config by deleting the  # . 

And yes your problem is quite simple.....you ahve 2 different lines trying to do 2 things to the same partition.

**try this**

**1.**Open a terminal and type - [COLOR="SeaGreen"]sudo mkdir /media/windows[/COLOR] - don't worry if it says the directory already exsists.
**2.** then type [COLOR="SeaGreen"]sudo gedit /etc/fstab[/COLOR]
**3.** erase everything and replace it with the following.....
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```
**4.** Save that file, close gedit and in the terminal type [COLOR="SeaGreen"]sudo mount -a[/COLOR]
**5.** Now to access your windows partition simply open up a terminal and type [COLOR="SeaGreen"]cd /media/windows[/COLOR] . Or if you restart your computer a new entry will be listed in the 'Places" menu called windows or something like that. 

If you still can't access your drive restart your computer, that will definatley make it work.

---

