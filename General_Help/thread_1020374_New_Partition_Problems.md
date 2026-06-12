---
title: "New Partition Problems"
date: 2008-12-24
forum: General Help
---

### Post by elanning on 2008-12-24
Greetings to all,

I recently deleted the NTFS partition from my laptop which was running a dual boot between WinXP and Ubuntu 8.10 because I had no further need for windows.  I then created a new partition in the vacant space, formatted it as ext3, and assumed I would be able to use it without any issues.

However my system now lists this new partition as unmounted, and even when I mount it and open it the only item in there is a folder called "lost+found" that has a grey "X" in the upper right of the icon?  And I am unable to write to the partition.  I used GParted to do the partition work.  

Any suggestions why this volume is not being automatically mounted and made ready for normal use?  On the information below, the partition that I am having trouble with is the last line "New"

Thanks.

Filesystem Size Used Avail Use% Mounted on
/dev/sda7 6.1G 3.0G 2.8G 52% /
tmpfs 1012M 0 1012M 0% /lib/init/rw
varrun 1012M 304K 1012M 1% /var/run
varlock 1012M 0 1012M 0% /var/lock
udev 1012M 2.8M 1009M 1% /dev
tmpfs 1012M 444K 1011M 1% /dev/shm
lrm 1012M 2.0M 1010M 1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6 42G 21G 20G 52% /home
/dev/sda1 43G 180M 41G 1% /media/New

---

### Post by plucky on 2008-12-24
Please post terminal output of ```
cat /etc/fstab
``` Possibly a permissions or ownership problem


See Psychocats [Mounting linux Partitions](http://www.psychocats.net/ubuntu/mountlinux)


Good Luck

---

### Post by Tim Sharitt on 2008-12-24
You will need to add an entry to /etc/fstab for the new file system.
Hit Alt-F2 and enter:
```
gksu gedit /etc/fstab 
```

Then insert a line for your new filesystem, some thing like:
```
/dev/sda2    /media/usr_data   ext3  auto,users,rw,relatime   0 0
```

This post has just about every thing you need to know about mounting and using filesystems: [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by elanning on 2008-12-24
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=2671da96-9baf-4ac2-b606-7d331c942797 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=adb5f339-8006-4f8c-ac73-11f0beb02e97 /home           ext3    relatime        0       2
# /dev/sda5
UUID=62618703-e608-40ee-83dd-a40109848b9e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


[http://picasaweb.google.com/lh/photo/T72oURdQYD1VzqDbF_f8bw?authkey=lOhGpF0JVy8&feat=directlink](http://picasaweb.google.com/lh/photo/T72oURdQYD1VzqDbF_f8bw?authkey=lOhGpF0JVy8&feat=directlink)

Opening up a properties dialogue it says I am not the owner, but I created it, how can I not be?

---

### Post by logos34 on 2008-12-24
plucky gave you the answer above--read the psychocats page (->especially the bottom).  you need to chown and chmod it

---

### Post by elanning on 2008-12-24
I tried that, ran the following commands:

sudo chown -R elanning:elanning /media/New/
sudo chmod -R 755 /media/New/

Following those commands, the little "X" that was on the icon for that lost+found folder was gone, but it still had the options to create like a new folder greyed out, and claimed I was not the owner.  

But now I am able to copy files to it, which I was not before...So one step forward but one step back I guess?

:(

---

### Post by logos34 on 2008-12-24
try adding an fstab line for /media/New.  Unmount and remount it.

---

