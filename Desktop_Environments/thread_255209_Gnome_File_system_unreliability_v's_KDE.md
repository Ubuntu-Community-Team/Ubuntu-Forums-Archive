---
title: "Gnome File system unreliability v's KDE ?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by jethro10 on 2006-09-11
Hi,
Been running linux since March and have just discovered a problem.
I thought it was my wireless network where copying files to a NAS disk would only go in small chunks, say 1-2Gb at a time before giving "Time out" errors. However this weekend I started to use a large USB hard disk for backing up (yes i'm paranoid) and it also failed in the same way. So it probably wasn't my network.

so my wife suggested installing KDE and trying it. I thought the filesystem underneath it all was the same and was skeptical but it backed up to both the NAS disk and the USB disk in one go (about 60Gb) without failing.

so can someone help me to understand which bits are shared by the two desktops above the kernel that may help me to understand this?

Anyone any ideas?

Only clue I have is that KDE copying especially to the USB disk is a whole magnitude quicker that Gnome's Nautilus.

I dont want to go KDE as I have no massive desire to deviate from the Cononical's chosen standard, Gnome seems more popular so thats all I want to learn. However for the time being, a backup in KDE once a week isn't hurting me.

Jeff

---

### Post by lukew on 2006-09-11
Hay,

I used to get errors through windows when copying onto discs; read write delay failure. The solution was to turn off disk caching. Under gnome/ubuntu dapper everything just works!!

Well...

What filesystem is on the disc? Perhaps you could check for errors through linux, my vfat disc was turning readonly after cp and rsync write transactions onto the disck even though I could copy and make directories on there.

[http://ubuntuforums.org/showthread.php?t=253621](http://ubuntuforums.org/showthread.php?t=253621)

I hope this helps, but seeing as you say it works on KDE and not on Gnome it might not.

Luke

---

### Post by jethro10 on 2006-09-11
> **lukew said:**
> Hay,

I used to get errors through windows when copying onto discs; read write delay failure. The solution was to turn off disk caching. Under gnome/ubuntu dapper everything just works!!

Well...

What filesystem is on the disc? Perhaps you could check for errors through linux, my vfat disc was turning readonly after cp and rsync write transactions onto the disck even though I could copy and make directories on there.

[http://ubuntuforums.org/showthread.php?t=253621](http://ubuntuforums.org/showthread.php?t=253621)

I hope this helps, but seeing as you say it works on KDE and not on Gnome it might not.

Luke
I'll take a look
I've done the obvious like checking for errors.

The NAS disk format is unknown to me, but presents itself to the world as a windows/Samba share. The Wifes XP PC works fine with it though, also.
The USB one is formatted as ext3 

Ta
Jeff

---

