---
title: "I do not detect the other partitions"
date: 2008-05-07
forum: Desktop Environments
---

### Post by Plath on 2008-05-07
I installed xubuntu 8.04 (32bit), and I cant detect the other partitions. I have 2 other OS on that computer (Ubuntu 8.04 (64bit) and windows), When I boot on Ubuntu 8.04 I am able to see the other partitions.

  Why I can't see the other partitions on Xubuntu 8.04 when I can do it on Ubuntu 8.04 ? I should add that Xubuntu 7.10 was able to see the other partitions.

  Any help ?

---

### Post by live2learn on 2008-05-07
I know you can't see it in desktop, but can you see it in thunar file manager. there was an error related to this in the beta version of xubuntu 8.04 and I don't know if its fix or not. 

try 

sudo fdisk -l 
in the terminal to see if the hd is there.

---

### Post by Plath on 2008-05-07
No, I can't see these partitions throught thunar.

  When I do " sudo fdisk -l " I have that :

[http://pastebin.ca/1011214](http://pastebin.ca/1011214)

  The 2 disks and the Partitions look like to be detected.
How to make thunar being able to see and mount the other partitions ?

  ( Thunar already detects USB keys )

---

### Post by Person98 on 2008-05-07
yeah i have the same thing, i have just been using nautilus, it works so i think it is a thunar problem

---

### Post by Plath on 2008-05-07
> yeah i have the same thing, i have just been using nautilus, it works so i think it is a thunar problem

  I tested this, it works. But it is strange that the thunar of the 8.04 can't see partitions when the thunar of 7.10 worked fine for that. I think this is a problem that should be fixed.

---

### Post by Person98 on 2008-05-07
yeah that is true, it did happen with the update, are you sure that a new version of thunar wasn't included with hardy though?

---

### Post by live2learn on 2008-05-08
hi plath it looks like that the partition is detected.
first try the easy way by navigating to the partition in thunar
in the root folder --then--> media and check the folders there.
/media/cdrom       
/media/disk1
/media/disk2 etc.
if you can't see anything then cdrom and floppy etc.
then you have to add them in, but it should be there.

if not then you have to edit the fstab settings.
root folder --> etc --> fstab. backup this file. 
then open it with a text editor and add the partition inside it.
I think you want the sda2 and sda3 partition to show which is windows file ntfs.just add a line similar to this below

# /dev/sda2 --the line with # symbol is just for notes
UUID=4484CBD584CBC79E /media/disk  ntfs-3g  defaults   0  1	   	

to find the UUID for the partition type this on the terminal.
ls -l /dev/disk/by-uuid

these numbers are just identification numbers for the partition.
the second colum /media/disk/  is the location of the folders of
the partion. the rest is default settings for read and write access.

it should create the folders automatically if you change it in the fstab file.But if it dosn't then you should create it.
automatically it creates disk1 disk2 etc. but you can
create this yourself with other names such as win_xp1
but the names must be the same one in fstab file

even if you get access the partition might not show up on desktop
but this is as simple as create a shortcut there.

---

### Post by Plath on 2008-05-08
live2learn , This does not work. Thunar didn't have access on the other partitions with these lines added to fstab (with the good UUID).

  It is strange but when I launch nautilus and I mount the other partitions, and when I launch thunar after then Thunar become able to see the other partitions in /media !!

---

### Post by live2learn on 2008-05-08
its good that you got it going somehow.
It didn't have access to the partition was the error
because the folder was not created automatically.
what was the error you had?

it also needs a reboot for changes to take effect.
then check if the folder is created in /media/your_foldernameInFSTAB.

your fstab file should look something like this.
here is the old fashion way of mounting your windows partition
without the UUID. But I believe you got it right but the access numbers
could be wrong at the end.

/dev/sda1      /media/disk1   fat16     defaults   0     1
/dev/sda2      /media/disk2   ntfs-3g   defaults   0     1
/dev/sda3      /media/disk3   ntfs-3g   defaults   0     1


here is the detail info links.
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

thanks for that info that thunar finds it when you install nautilus
file manager. 

the simple work around here is to install nautilus.
:lolflag:

---

### Post by theDaveTheRave on 2008-05-08
interesting thread guys.

I've just noticed that when I downloaded the current updates I was being told I only had 30.1GB.

I then remembered that I had partitioned my disk into 2 halves during instalation.

but now how do I find where all my disks are and what size they are and the space available on each?

A quick note on UUID and editing the fstab. There is a great thread (I think by Bodi Zazen) on editing the FSTAB.

One thing that I noticed was that when I dual booted (before going totaly over to Hardy), was that I often had to log into the Windows partition. If I did this I often found I ended up with "issues". This would result in failures when I later logged into ubuntu.... I still don't understand what was going on.... but I had to do a "hard reboot" this seemed to changed the details of the UUID of the various disks that I had inside the machine. Preventing me from being able to access my windows partition as the UUID had changed.

anway just thought I would add that detial.

Dave

---

### Post by live2learn on 2008-05-11
******Warning ******
If you install X,K,E & UBUNTU 8.04 and above with windows using wubi then the above instructions would not work. but its a good learning curve.

So please search for wubi fstab instead.

thanks

---

