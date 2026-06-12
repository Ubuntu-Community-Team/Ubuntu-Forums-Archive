---
title: "Today's upgrades broke stuff"
date: 2006-01-28
forum: Desktop Environments
---

### Post by seakiwi on 2006-01-28
Sheesh ...

Just when I have things set up and working perfectly, I decide to upgrade some suggested upgrades and now several things are appear to be broken  :( 

Firstly, with some help from people here a few weeks back and from this article: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

I managed to set my Windows drive to mount automatically at boot up, so that it was always visible and accessible. Suddenly, today it is no longer mounted or visible and I have no idea why. Same thing goes for my CD drive -  as I undertand it, the latest version of Kubuntu/KDE auto mounts the CD drive so that one doesn't have the hassle of all that mounting/unmounting. It was working fine yesterday when I played some audio CDs. Today, it's no longer mounted automatically and not even visible.

My fstab looks the same as it always did from memory. Can someone take a look at it please and let me know if you see anything that's obviously wrong there?

[I]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hda2       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/I]


I've tried re-doing that instructions in the above article to get my Windows drive "back again" but the settings it tells me to add to my fstab are already there.

This is so discouraging ... I've spent so many hours learning and asking questions and getting my head around how to do all this, and just when I think I've "got it" I strike weird glitches like this. Everything was working fine until this morning's upgrades.  I have no idea whether it's related or not but it seems pretty weird that things should suddenly 'break' shortly after upgrading stuff.

Can someone please help me get these two things fixed? 

Many thanks!

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=seakiwi]Sheesh ...

Just when I have things set up and working perfectly, I decide to upgrade some suggested upgrades and now several things are appear to be broken  :( 

Firstly, with some help from people here a few weeks back and from this article: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

I managed to set my Windows drive to mount automatically at boot up, so that it was always visible and accessible. Suddenly, today it is no longer mounted or visible and I have no idea why. Same thing goes for my CD drive -  as I undertand it, the latest version of Kubuntu/KDE auto mounts the CD drive so that one doesn't have the hassle of all that mounting/unmounting. It was working fine yesterday when I played some audio CDs. Today, it's no longer mounted automatically and not even visible.

My fstab looks the same as it always did from memory. Can someone take a look at it please and let me know if you see anything that's obviously wrong there?

[I]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hda2       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[/I]


I've tried re-doing that instructions in the above article to get my Windows drive "back again" but the settings it tells me to add to my fstab are already there.

This is so discouraging ... I've spent so many hours learning and asking questions and getting my head around how to do all this, and just when I think I've "got it" I strike weird glitches like this. Everything was working fine until this morning's upgrades.  I have no idea whether it's related or not but it seems pretty weird that things should suddenly 'break' shortly after upgrading stuff.

Can someone please help me get these two things fixed? 

Many thanks![/QUOTE]

Can you check if the device is still called the same thing?  E.g. try:
```

$ sudo cfdisk /dev/hda

```
And make sure that hda2 is still the NTFS partition.  Not sure what could have broken your mount points.  Do you have any idea what was upgraded?  Try going into synaptic and look under File -> History to find out what the packages were.  Maybe that will give us a clue.

Thanks.

---

### Post by seakiwi on 2006-01-28
[QUOTE=cwaldbieser]Can you check if the device is still called the same thing?  E.g. try:
```

$ sudo cfdisk /dev/hda

```
And make sure that hda2 is still the NTFS partition.  Not sure what could have broken your mount points.  Do you have any idea what was upgraded?  Try going into synaptic and look under File -> History to find out what the packages were.  Maybe that will give us a clue.

Thanks.[/QUOTE]

OK, I have no idea how I fixed it, but the Windows mounting problem is fixed. I can now access my mounted Windows partition. I'll reboot a bit later and check that it "sticks" on a restart.

The CD thing is still weird. I have no idea what's going on with it. I can see it in /media along with all the other drives, but when I try to play a CD I get an error about permissions. I've checked the permissions on the CD writer and they are root only. I'm guessing that's not right. How do I change the permissions to make it available to all users. Given that this machine is only used by me, making it accessible by all users seems to be the safest idea.

Hopefully if I change those permissions it might let me use it again. Meanwhile I'll go take a look at my synaptic history and see if there's anything there that looks related.

Thanks for your help! :)

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=seakiwi]OK, I have no idea how I fixed it, but the Windows mounting problem is fixed. I can now access my mounted Windows partition. I'll reboot a bit later and check that it "sticks" on a restart.

The CD thing is still weird. I have no idea what's going on with it. I can see it in /media along with all the other drives, but when I try to play a CD I get an error about permissions. I've checked the permissions on the CD writer and they are root only. I'm guessing that's not right. How do I change the permissions to make it available to all users. Given that this machine is only used by me, making it accessible by all users seems to be the safest idea.

Hopefully if I change those permissions it might let me use it again. Meanwhile I'll go take a look at my synaptic history and see if there's anything there that looks related.

Thanks for your help! :)[/QUOTE]

Not sure why, but I used to have a /dev/cdrom link to /dev/hdc, but it disappeared.  I changed apps that were using it (like amarok or grip) to use /dev/hdc instead, and everything was fine.

---

