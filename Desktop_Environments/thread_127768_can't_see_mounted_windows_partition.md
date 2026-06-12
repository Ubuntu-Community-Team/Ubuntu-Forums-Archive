---
title: "can't see mounted windows partition"
date: 2006-02-09
forum: Desktop Environments
---

### Post by hyperpsyched on 2006-02-09
It seems that I can no longer see my shared vfat partition in /media when in user mode using Konquerer... 

I can see it just fine as root using Konquerer when I browse to /media but when I switch to user mode they disappear. I tried unmounting and remounting and also setting all permissions (using the filesystems gui) for rw permissions for user. 

Am I doing something really obviously stupid here. Help!  :confused:

---

### Post by aysiu on 2006-02-09
See the fourth link of my signature.

---

### Post by FlakJacket on 2006-02-09
I don't think he means mounting it.  Can you access it just using the actual directory not the virtual folder media:/ ?  I think he just isn't seeing the drive in media:/ but he can still access it and mount it but I could be wrong.

Flak

---

### Post by SectionThree on 2006-02-09
Here's an out-of-left-field idea (it works pretty well for us ppc users, it might work for you i386 users too, who knows)...

Anyway, if you have a Windows-Ubuntu dual-boot scheme, boot up into Windows and give everybody (owner, groups and guest) permission to do everything (read, write & execute) on the vfat volume you want to mount.

I'm not guarenteeing anything (I'm running a dual-boot scheme with Mac OS X/Ubuntu, and I did something similar to mount an HFS+ volume), but it's worth a try.  Nothing ventured, nothing gained, hey?

---

### Post by hyperpsyched on 2006-02-10
Tried manually changing the fstab file but no luck... this gets even wierder though. 

In Konquerer ALL mounted devices are totally invisible... no visible files, folders, etc... 

but when I use firefox I can see they are mounted no problem, even in user mode which is how I am logged in now. 

So this must be a problem with Konquerer... does that help at all?

Sorry for the late reply. It was 2 am in Berlin when I finally turned the computer off.

Maybe I should post again with a new description of the problem? Mounted devices visible in firefox but not in Konquerer?

---

### Post by GoldBuggie on 2006-02-10
do a ```
sudo adduser hal disk
```. Reboot and enjoy seeing your media in media:/

---

### Post by hyperpsyched on 2006-02-10
By the <hal> in your 'sudo adduser' command do you mean the name of the user I want to add or do you literally want me to type hal in there.

I am not taking any chances...  lol

---

### Post by hyperpsyched on 2006-02-10
really a little lost... I assume hal is the user name I want to add but there is no group disc? What I am I doin wrong?

---

### Post by GoldBuggie on 2006-02-10
just type it as i wrote. hal becomes the user and it is added to the disk group.

---

### Post by GoldBuggie on 2006-02-10
and i know that there isn't a group name disk.(observe NOT disC but disK) it will be vreated when you do this

---

### Post by hyperpsyched on 2006-02-10
OK... so I typed it in and yes... I can see the discs in both media and my desktop. This is ok but they have odd names like "4.2G Media" and "OGD17HJ8...blah blah" and I certainly don't remember mounting anything by that name. So two questions.

1. Is there any way of removing the icons from my desktop?
2. If not, is there anyway of renaming them to something a little more human?

---

### Post by GoldBuggie on 2006-02-10
1: righ click desktop->config desk.->behaviour->device icons
2: f2 or righ-click-> properties and rename

---

### Post by hyperpsyched on 2006-02-10
You really have had way too much ubuntu. It worked by the way.... I feel a bit the dork.

One more question.

Can I remove/hide the NTFS partition icon from the desktop?

---

### Post by GoldBuggie on 2006-02-10
well removing specific hd's isn't possible i think. removing samba shares if you have your ntfs on another computer is possible(righ click desktop->config desk.->behaviour->device icons)

another way is to not show any mounted harddrives and right-click on desktop and goto *create new->link to device* and add the harddrives you want to show on your desktop

---

