---
title: "10gb unallocated space"
date: 2006-04-15
forum: Desktop Environments
---

### Post by 146lily on 2006-04-15
Cloned my old hdd to new using tool from ultimate boot cd (from mrbass) in 30min. used dapper disc in repair mode to fix grub in 5min. What's the best way now to use extra unallocated space on the new larger hdd. I'm still a bit new to Linux and can create an extra formatted partition using gparted but permissions stop me using it.

-------edit-----------
notes:

Attach new hdd as slave on ide cable with hdd to be cloned as master.

Download and use free clone tool is g4u v2.1 (very fast) on ultimate boot cd v3.4 from [http://www.mrbass.org/](http://www.mrbass.org/)

Use ubuntu or kubuntu installation cd in repair mode to fix grub loader and enable boot.

Download and use free gparted live cd from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) to change free space into a formatted partition. The live cd works best because the operating system is not running.

I used a kde disk and filesystem gui to mount partition and place entry in fstab, the skilled can use the terminal of course.

If needed use terminal to change partition permissions using the chmod (google bash commands) command.

It takes about an hour (20gb drive to 30gb) to complete the above process if you now what your doing, which I didn't! 

Hmm nice little experiment!

----edit------

---

### Post by Ramses de Norre on 2006-04-15
Permissions keep you from using it? Maybe your mount options aren't correct then..

---

### Post by 146lily on 2006-04-15
Dont know much about it, tried ext3 file sytem (is this right?) when formating and had to choose primary partition, no other options. 

What should a general music and video (data) file partition look like?
Is it like windows were I could have many data partitions but only one active partition?

---

### Post by Ramses de Norre on 2006-04-15
You can have a max of 4 primary partitions, but you can also make extended ones (that count for one primary each) and inside such an extended partition you can then make a lot of logical partitions (which behave quiet the same as primary ones).
And you can have more than one active partition, but you'll need to use a bootloader then (in a dual boot you've got two active partitions).
ext3 is perfect for data storage, to browse it you'll need to make an entry for it in /etc/fstab.
Ask if you need help with that.

---

### Post by 146lily on 2006-04-15
The partition is there to be browsed but it is owned by root and I can't write to it?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 auto ,atime,noauto,ro,dev,exec,suid,users 0 0
/dev/hde /media/cdrom auto ,atime,noauto,rw,dev,exec,suid,users 0 0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,users 0 0
/dev/hda3 /hda3 ext2 ,atime,auto,rw,nodev,noexec,nosuid,nouser 0 0

does nosuid, nouser need changing

---

### Post by Ramses de Norre on 2006-04-15
Did you make a line for it in fstab?
Do sudo gedit /etc/fstab and add a line like this at the bottom:
```
/dev/hda4       /home               ext3    nodev,nosuid 0       2

```
Where hda4 is the partition number and /home the mountpoint, if you take a mountpoint under /media you can get an icon automaticaly in the places menu and on your desktop.
Create the mountpoint before mounting with mkdir or sudo mkdir and when the fstab is saved do sudo mount -a

---

### Post by 146lily on 2006-04-15
It would be better if I could make hda1 bigger to use up free space.

---

### Post by Ramses de Norre on 2006-04-15
You can do that but you'll need to use a live cd, you can't change mounted partitions. A gparted live cd or knoppix is very good for this.
Be sure to make back ups!

---

### Post by 146lily on 2006-04-15
I'm losing the plot, I don't know how many partitions I have 3 or 4. I thought gpart created an entry in fstb but maybe not, I will use both methods, this is about learning.
](*,)

---

### Post by Ramses de Norre on 2006-04-15
Gparted makes the partition, which you then have to mount (and by using fstab it will be mounted on boot up).
How many partitions you have can easily be seen with gparted: how many of those separate colored blocks are on the drive.

---

### Post by 146lily on 2006-04-15
this is the 10gb 

/dev/hda3 /hda3 ext2 ,atime,auto,rw,nodev,noexec,nosuid,nouser 0 0

---

### Post by Ramses de Norre on 2006-04-15
Are you sure it's ext2? ext3 is quiet better for fixed disks.. (it has journalling)
I don't know all the options you use, but I'd stick to the defaults if possible.

---

### Post by 146lily on 2006-04-16
Hmmm, like any ex-windows user I went and found a gui {kde disk+filesystem}  which wrote the line in fstab....however I had to then use the terminal and bash command to change user from root to me ie chmod. Had a look at resizing ext3 partitions....no luck yet. Anyway a data partition is fine. 
Conclusion: I can clone a hardrive using linux, if unallocated space is left on my drive this can be made into a data partition...fine!

---

### Post by Ramses de Norre on 2006-04-16
4 months ago I was still a windows only user, but now I can do much more with the command line than with the regular GUI. It's just about getting used to it ;)
How did you try to resize the ext3 partition? You'll need to use a live cd to edit your / partition because you can't modify mounted partitions.

---

### Post by 146lily on 2006-04-16
I used the gparted live cd you recommended and also system rescue disk [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) using qtparted but never got anywhere. Will try again today, resizing ext3 partitons is useful!

---

### Post by Ramses de Norre on 2006-04-16
You should be able to select the ext3 partition and choose resize.
Of course you can't enlarge it if the unallocated space isn't situated right after the existing ext3. If that's the case you'll need to move the existing partitions around to get it right.

---

### Post by 146lily on 2006-04-16
That may be the problem, my swap partition is in the way, I need to move it....hmmm how?

I'm enjoying this and thank you for the help!

part 2 resize the partition coming up next! :-D

---

### Post by Ramses de Norre on 2006-04-16
sudo swapoff -a 
This will disable swap, if your low on ram your machine will go terrible slow so if that's the case close first all other applications but gparted and after moving the swap partition do sudo swapon -a to enable it again.
If you've got enough ram you probably wont even notice a difference.

---

