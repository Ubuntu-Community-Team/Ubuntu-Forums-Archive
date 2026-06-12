---
title: "Help cannot access NTFS partition"
date: 2006-01-27
forum: Desktop Environments
---

### Post by quinton on 2006-01-27
Hi,

I just installed ubuntu. Am liking the interface... will likely try out KDE too, buti got a bigger problem at hand 1st. i've got my 2 other NTFS partitions sda1 and sda2 on the desktop. however when I double click on them, i get this error msg:

"The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "sda2"."

I don't really know how to access my ntfs partition now. My WinXP does have a log in as an administrator, cld that be a problem? if so how do i solve it? Any ideas?:confused: 

Thanks a lot guys![-o< 

 On a sidenote, i get this idea that linux cannot write to NTFS? it can only read?

---

### Post by frodon on 2006-01-27
Yes, only read access with NTFS under linux, for your issue follow this link : [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by Who on 2006-01-27
Righty,
Welcome, good luck!

You are right, at the moment Linux can only read from ntfs officially and safely. There are some ways to do it but I wouldn't reccomend hem. Google will show you the way (ntfs linux read write). Unfortunately Windows doesn't natively support mounting Linux file systems, so if you haven't already got one I would reccomend creting a fat32 partition for swapping data between the two systems.

As for mounting (allowing you to access the folders on the disk by putting them inside a folder on the root file system (called "/")) your NTFS disks:
There is a file on your system called fstab (file system table, as I remember it) and it describes the options that each disk is 'mounted' with. The most direct way to fix your problem should be to edit this. so, open a terminal and 
sudo cp /etc/fstab /etc/fstab_backup_[*date*]
this creates a backup of the odl file that you can replace the real fstab with if all goes wrong. the 'sudo' command gives you super user privelidges for the commands typed afterwards (in this case, cp (= copy))

then type

sudo gedit /etc/fstab

gedit is a Gnome notepad/text editor

Now, look at the line for your ntfs disks will be type ntfs) - you could post it here if you are not sure what to do.
This page should help you understand what it all means (even though most of it applies to Gentoo:
[http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#.2Fetc.2Ffstab](http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#.2Fetc.2Ffstab)

aaannyway

The options you want in /etc/fstab for the drives are
nls=utf8,umask=0222
so it will look something like 
/dev/hda5 /media/windows ntfs nls=utf8,umask=0222 0 0

now at the command line type
sudo mount -a

to remount all the disks and try to read the disks. 

It _ought_ to work :P

Good Luck

Who

---

### Post by quinton on 2006-01-27
thanks lots for the help! it worked ;) tho I needed to restart the computer and not just remount all drives. :p

---

### Post by Arles on 2006-01-29
Hello guys I-m new to Ubuntu too and for me it didn't work. When I entered the sudo mount-a I got the message: ```
mount: special device /dev/hda1 does not exist

```

this is a copy of my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               reiserfs notail          0       1
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/sdb1       /media/sdb1     ntfs    defaults        0       0
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows ntfs umask=0222 0 0
```

Please help me. SDA1 is mz windows partition and SDB1 is another harddisk in NTFS format where I keep al my stuff.

---

### Post by RaisedFist on 2006-01-29
Delete this line from /etc/fstab:
**/dev/hda1 /media/windows ntfs umask=0222 0 0**

---

### Post by Arles on 2006-01-29
I can see my winpartition now... TNX

The second problem is that I still can't open the other ntfs harddisk (sdb1)

this is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               reiserfs notail          0       1
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/sdb1       /media/windows2  ntfs    nls=utf8,umask=0222 0       0
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by Who on 2006-01-29
That is a  bit of a mystery! both the hard disks are being mounted with the same options - so if you can't access them both I would guess that the problem is with file permissions (though I _thought_ umask=0222 would sort that out...?)

A good test that would give us some useful info would be to type this at a terminal

sudo nautilus --no-desktop 

and then navigate to /media/windows2 and see if you can browse the files as a super user.

Good Luck

Who

---

