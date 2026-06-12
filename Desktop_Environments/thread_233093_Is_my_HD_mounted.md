---
title: "Is my HD mounted?"
date: 2006-08-09
forum: Desktop Environments
---

### Post by LostHere on 2006-08-09
Sorry, not worth my time. Going back to XP and the world of point and click. :-D

---

### Post by randell6564 on 2006-08-09
> **LostHere said:**
> Hi,

I am so lost. My system: Ubuntu on my Master HD. I have a second HD(that was connected when I installed Ubuntu) as slave that is formatted NTFS and has lots of text, video, music, picture files on it. I took out my XP HD so this is not a dual boot system. But I can't access my 2nd HD. 

What I would like to be able to do is have an icon on my desktop that I can just double click to get to my files on my 2nd HD. When I go into Disk Manager I get the following:

2. Select the correct hard disk, and click the Partitions tab.
It says, /dev/hdb1
Windows NTFS
access path: /tmp/disks-conf-hdb1
Status: Accessible
But when I click on Browse I get "The folder contents could not be displayed> You do not have the permissions necessary to view the contents of "disks-conf-hdb1"

I noticed under /tmp/disks/-conf-hdb1 that there is a lock icon.

Is this HD mounted? Why does it say "Accessible"?  I thought Ubuntu could read HDs that were connected during the installation. If not, how do I mount it. I've read, and read, and read some more, but I am so lost. Help.
](*,) :-k :( :mad: ](*,)

Please post your /etc/fstab

If your ntfs partition is not in your /etc/fstab, you will not be able to access it.
Check out this link [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by mg3kc on 2006-08-09
The drive needs to be in the fstab file (/etc/fstab)... 

For a short term fix, you can mount the filesystem using the following instructions: 
open a terminal window
cd /mnt
sudo mkdir old_files (or whatever you want to call it)
sudo chmod 0550 old_files
sudo mount /dev/devicename (hdb1 probably) /mnt/old_files

This will allow you to access your files but *not* write anything on the drive. This is because I am still not used to linux being stable with NTFS. Maybe we can all write on NTFS partions now.

I will try and paste up a copy of my fstab to show you how to make the mount option permenant.

---

### Post by randell6564 on 2006-08-09
> **mg3kc said:**
> 
Maybe we can all write on NTFS partions now.


There is supposedly applications out there now that enable one to write to NTFS.  However, they are still in the testing stages, so I would not recommend trying!

---

### Post by LostHere on 2006-08-09
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Also what do I need to do to change the xorg.conf file? My back button on my mouse doesn't work, I found a thread, changed the file, but got an error message.

Thanks

---

### Post by mg3kc on 2006-08-09
> **LostHere said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Also what do I need to do to change the xorg.conf file? My back button on my mouse doesn't work, I found a thread, changed the file, but got an error message.

Thanks

Add the following line... that should help
/dev/hdb1       /mnt/old_files   ntfs    defaults,nls=utf8,umask=007,gid=46 0

replace /dev/hdb1 with the location of your hard drive (if different).
replace /mnt/old_files with where you want the drive mounted.
dont forget that the directory that you want to mount on needs to exist before you try and mount it... 

HTH

---

### Post by mg3kc on 2006-08-09
> 
Also what do I need to do to change the xorg.conf file? My back button on my mouse doesn't work, I found a thread, changed the file, but got an error message.


in a terminal window...

sudo gedit /etc/X11/xorg.conf

That will give you write permissions.

---

### Post by randell6564 on 2006-08-09
> **LostHere said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Also what do I need to do to change the xorg.conf file? My back button on my mouse doesn't work, I found a thread, changed the file, but got an error message.

Thanks

there is your problem! You need to add your NTFS, or Fat32 partitions!
Use this [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)  Scroll down to #15 Windows and follow the instructions.

As for xorg, cant help ya, sorry!

---

### Post by LostHere on 2006-08-09
Where is the love???

I opened a terminal, typed in:

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/dev/hdb1 /mnt/old_files ntfs defaults,nls=utf8,umask=007,gid=46 0

A window opened that said, "hdb1(/etc/dev)" with tabs that said, hbd1, old files, ntfs, defaults nlf=utf8,unmask=007,gid=46, 0.

I clicked on each tab and there was nothing in them. I clicked close, it said save changes(what changes?) I said, Yes, and I got this error message: Could not save the file /etc/dev/hdb1. Unexpected error: File not found

Now what? Am I to change old_files to something else? I have a folder on my desktop called, "My Computer" and in that folder I have a folder called "My 2nd Hard Drive NTFS". When I click on that folder, that is where I want the contents of my 2nd HD to be. 
](*,) ](*,) ](*,) ](*,)

---

### Post by randell6564 on 2006-08-09
> **LostHere said:**
> Where is the love???

I opened a terminal, typed in:

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/dev/hdb1 /mnt/old_files ntfs defaults,nls=utf8,umask=007,gid=46 0

A window opened that said, "hdb1(/etc/dev)" with tabs that said, hbd1, old files, ntfs, defaults nlf=utf8,unmask=007,gid=46, 0.

I clicked on each tab and there was nothing in them. I clicked close, it said save changes(what changes?) I said, Yes, and I got this error message: Could not save the file /etc/dev/hdb1. Unexpected error: File not found

Now what? Am I to change old_files to something else? I have a folder on my desktop called, "My Computer" and in that folder I have a folder called "My 2nd Hard Drive NTFS". When I click on that folder, that is where I want the contents of my 2nd HD to be. 
](*,) ](*,) ](*,) ](*,)

K., chill out pickel! lol!  Post your /etc/fstab  lets do this one step at a time.

---

### Post by LostHere on 2006-08-09
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

BTW, I have a DVD burner, and a CD Burner. I believe they are on the secondary ribbon thingamajing. DVD burner would be the master.

---

### Post by randell6564 on 2006-08-09
> **LostHere said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

BTW, I have a DVD burner, and a CD Burner. I believe they are on the secondary ribbon thingamajing. DVD burner would be the master.

K.,Like I said before, your Windows partitions are not there!

Follow the link that I gave you and then come back and present your issues, if any!

It's not "sudo gedit /etc/dev/hdb1 /mnt/old_files ntfs defaults,nls=utf8,umask=007,gid=46 0"


it's /dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
Thats assuming that your NTFS is HDA1!  This is what you would add to your /etc/fstab!

Look.,here is my /etc/fstab

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/windows vfat  iocharset=utf8,umask=000  0    0[/B]

---

### Post by LostHere on 2006-08-09
Sorry, but linux is not worth my time. Going back to the world of point and click.

---

### Post by randell6564 on 2006-08-09
> **LostHere said:**
> Sorry, but linux is not worth my time. Going back to the world of point and click.

AAH! just a drive-by huh? Figures.

---

