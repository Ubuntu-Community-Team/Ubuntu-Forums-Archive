---
title: "Mounting error in Nautilus"
date: 2005-11-17
forum: Desktop Environments
---

### Post by dmh-bidlah on 2005-11-17
I'm running Ubuntu Breezy, which was originally a Kubuntu, but I grew tired of KDE and installed ubuntu-desktop. The problem is that when I put a DVD(Data) in the tray and close it, I am unable to go to it. When clicking on the CD/DVD combo device in Nautilus I get an error that pmount couldn't be executed. But when I mount the DVD from console using
```
mount /dev/dvd
```
I can go to it normally. The thing is I would like to get rid of that error so I could  mount the DVD from Nautilus.
I have pmount installed by the way.
And please don't suggest reinstalling, because I'm tired of constantly reinstalling my base system and then messing with the UID-s in my home directory.
Thanks for any help.

---

### Post by aysiu on 2005-11-17
[QUOTE=dmh-bidlah]I'm running Ubuntu Breezy, which was originally a Kubuntu, but I grew tired of KDE and installed ubuntu-desktop. The problem is that when I put a DVD(Data) in the tray and close it, I am unable to go to it. When clicking on the CD/DVD combo device in Nautilus I get an error that pmount couldn't be executed. But when I mount the DVD from console using
```
mount /dev/dvd
```
I can go to it normally. The thing is I would like to get rid of that error so I could  mount the DVD from Nautilus.
I have pmount installed by the way.[/quote] I don't know what pmount is, but can't you modify your /etc/fstab to have the proper permissions? I don't know how to do fstab entries for DVD-ROM drives, though. Maybe someone else here can chip in for that?

> 
And please don't suggest reinstalling, because I'm tired of constantly reinstalling my base system and then messing with the UID-s in my home directory.
Thanks for any help. If you find yourself doing frequent reinstalls (as I did when I first started learning Ubuntu/Linux), it may be worth it to set up a separate /home partition so that you won't have to mess around with stuff.

---

### Post by dmh-bidlah on 2005-11-18
Thanks for the reply. Here is my /etc/fstab, but I think that these removable drives got to /etc/mtab and are put there dynamically by some magic.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda7 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda5 /boot ext2 defaults,atime,auto,rw,dev,exec,suid,nouser 0 2
/dev/hda6 /home ext3 defaults,atime,auto,rw,dev,exec,suid,nouser 0 2
/dev/hda8 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
/dev/hda1 /media/windows ntfs noauto,uid=0,gid=0,auto,ro,nouser 0 0
Edasi-2:/home/joosep/  /media/Edasi-2/home/joosep   nfs      rw,hard,intr  0 0

```

[QUOTE="aysiu"]
If you find yourself doing frequent reinstalls (as I did when I first started learning Ubuntu/Linux), it may be worth it to set up a separate /home partition so that you won't have to mess around with stuff.
[/QUOTE]
I have had a separate /home since I started using linux, but when I reinstall I sometimes have to mess with the permissions, because I want to have the same username, but it won't initially allow me to create a username when there is a directory like this in /home already, but that is beside point. 

I recently discovered that I can **un**mount the DVD from Nautilus normally. And I can also mount it from console as a normal user, it's just that pmount doesn't work. I will see to my configuration files and be back later...

LATER:
When I run pmount from the console
```

pmount /dev/dvd

```
I get that i don't have permissions to eecute pmount. In the pmount man page i found out that i have to be added to the plugdev group, which i was not. But even after adding myself there I couldn't execute pmount. Most strange and confusing indeed...
I hope someone can help me...

---

### Post by aysiu on 2005-11-18
I don't know if this makes a difference, but in my /etc/fstab, this is the entry for my DVD-ROM drive: ```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
``` I've never had to mess around with pmount config files *and* I've never had a problem with a fresh install using the /home partition with the same username--that's the whole point of having a separate /home partition. Something's wrong, and I wish someone else would chime in here (someone more knowledgeable than I am).

---

