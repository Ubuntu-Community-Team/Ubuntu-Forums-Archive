---
title: "Want to put Ubuntu on main machine except one problem"
date: 2006-09-19
forum: Desktop Environments
---

### Post by JediSpam on 2006-09-19
I have enjoyed linux distros over the past year or so but I still have been running my main machine on windows. i am seriously considering changing my new machine to ubuntu but i have one problem. i have a 160 secondaryd drive full of media that i still want. how can i keep it when swapping my main drive to ubuntu? i'm assuming that 160gb is a "windows" formatted drive? i'm not sure what to do because i need that media. i always want to make sure someone has call of duty 2 fully working. thanks

---

### Post by mssever on 2006-09-19
You'll have to find out what the format of that drive is. If you're in Windows, do properties on the drive and it'll tell you.

Linux can read any Windows format. It can write FAT32 (which Linux calls vfat). You can also write to NTFS, but that involves quite a bit more setup.

When you run the installer, choose the manual partition option and don't let the partitioner reformat your media partition.

---

### Post by kick6 on 2006-09-19
Ubuntu can read from windows partitions.  If its formatted with fat32 you can even write to it.  When using the installer, chose manual partition editing, and leave your media partition alone!  Make sure to chose a mount location, and viola, you have all your windows media.

---

### Post by JediSpam on 2006-09-19
ok i guess i will try this. could i just unhook my secondary drive until i have ubuntu installed? i'm not sure what format i partitioned the secondary drive so i'm not sure if i can write on it or not. when you mean write you are saying add stuff to the drive or take away?

---

### Post by mssever on 2006-09-19
> **JediSpam said:**
> ok i guess i will try this. could i just unhook my secondary drive until i have ubuntu installed? i'm not sure what format i partitioned the secondary drive so i'm not sure if i can write on it or not. when you mean write you are saying add stuff to the drive or take away?

You can unplug your drive during the install if you want, but if you do so, you'll have to manually configure it after the install--including telling Ubuntu what the format is. So you need to know the format regardless--unless the installer is able to auto-detect that.

Writing to a disk means just what it implies: adding, deleting, or changing the contents.

---

### Post by JediSpam on 2006-09-19
ah ok thanks

---

### Post by jISh on 2006-09-19
Also, if you have the space on your primary drive, you could copy all the media over from the second drive. Then format the second drive using a LiveCD and the cfdisk command (ext3 is the best choice although that could be a huge debate between some junkies :P). Copy your stuff back then proceed to install.

No messing with awful filesystems afterwards!

---

### Post by JediSpam on 2006-09-19
definitely don't have the space lol. 36 gb raptor primary and 160gb secondary

---

