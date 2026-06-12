---
title: "Dual booting Q."
date: 2008-12-18
forum: General Help
---

### Post by BlackS3th on 2008-12-18
Hello there .. I had my laptop bought with vista and as all know ... F*** windows ... I installed ubuntu and i like it.:guitar: 

I have a problem though and i have to install windows back ... Im a gamer.

Now my friend gave me a cd to install ubuntu but my friend gone to another country now my request is...

To install windows back with the 2 cds that they gave to me when i bought the laptop but at the same time to keep ubuntu..

Tell me if i can and tell me what do i lose with dual booting (i mean like if my laptop loses its speed)

Thank you if you reply ... Damn you if you don't:lolflag:

PS: i cant afford losing ubuntu by booting windows ... my friend is gone so the ubuntu cd....

---

### Post by SuperSonic4 on 2008-12-18
You'll only lose hdd space on a dual boot and the only real way to install windows is to partition (I prefer gparted and other OSS stuff) a drive to give NTFS and install vista there. This will override your grub (but not your ubuntu installation if you partition correctly). To my knowledge there is no way to save grub. You can then use [[COLOR="Red"]easybcd[/COLOR]]("http://neosmart.net/dl.php?id=1") to put ubuntu back onto grub if it is vista you're installing

---

### Post by lovelyvik293 on 2008-12-18
You do not lose the speed because of the dual boot.Because only one OS works at a time.
For dual boot just install the windows on the patition other then the ubuntu one and then you have to install the grub again.
For installing grub with the live cd follow the link:-
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Chears.

---

### Post by BlackS3th on 2008-12-18
Ok got it but ... Is there any other way to play games properly rather than install windows again???... I have issues with windows (Im having viruses all the time from internet ... and if i use anti virus its just slowing me down ...and the worst part if i want to be fast and use anti virus i have to pay ... its just all for the money)

---

### Post by lovelyvik293 on 2008-12-18
You can use the Wine in ubuntu for playing some of the games in ubuntu.
Second option is to use the virtual machine in which you can install the windows and play games.

---

### Post by BlackS3th on 2008-12-18
Well that helped a lot thanks and im sure your gonna make a good advisor.

---

### Post by albinootje on 2008-12-18
> **BlackS3th said:**
> Ok got it but ... Is there any other way to play games properly rather than install windows again???... I have issues with windows (Im having viruses all the time from internet ... and if i use anti virus its just slowing me down ...and the worst part if i want to be fast and use anti virus i have to pay ... its just all for the money)

Check this software for playing windows-games in Linux :
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

It uses Wine (mentioned by another poster), but is meant to make things easier.

Wine is a cool project where volunteers worked on for more than 15 years, but it does not really have a consistent and easy application-installer included, and apart from that it can depend on the Wine-version for how well the games run.
PlayOnLinux tries to address that.

---

