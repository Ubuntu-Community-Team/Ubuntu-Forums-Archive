---
title: "Uninstall issues"
date: 2006-07-14
forum: Desktop Environments
---

### Post by bluezdood on 2006-07-14
Ok for one reason or another I needed to delete the Ubuntu partition of my hd, and expand the NTFS partition letting XP have control over my whole hard drive (for now).  Problem being that GRUB screwed up my MBR.  First, it wouldn't load anything since it was already erased, so I reinstall the XP os which is fine, but now I am prompted to choose between two Windows installs, anyone been through this and know how to fix it?  Also, since I had done this before, GRUB shows EVERY installation of Ubuntu, so I ended up with four entries, Ubuntu i386 x2, Ubuntu i686, and Windows XP.  Any help or guidance would be appreciated, especially since I plan on installing Kubuntu when I get the chance.

---

### Post by Landoln on 2006-07-14
Several things.  If you only want XP on your system and you want to return your MBR to just normal windows boot, boot up your windows xp install cd, and choose repair existing installation.  You can then log into the installation at the command line using your Administrator password.  Once you're at the dos prompt, type fixmbr (it may need to be in caps) and that will overwrite your mbr with just the windows loader and just allow you to get to the existing windows installs.

You can edit your Grub boot menu in Ubuntu by opening up the /boot/grub/menu.lst file (sudo nano -w /boot/grub/menu.lst) and commenting out (putting a # before) any sections that you don't want showing up.  

A suggestion for future installs, make a small partition (50MB or so) at the beginning of the drive and use that as you /boot partition.  then if you need to revert back to windows, or do whatever, you can leave that partition intact and grub will still be there to boot the remaining operating systems.

---

### Post by TheBlackNoodle on 2006-07-14
I haven't actually checked this out in Windows, but try Start->Run->msconfig. Click on the boot.ini tab. There should be a few entries there, one of them probably removable. I wouldn't try removing one right away, though, unless they both boot correctly. I'm going to go take a look at this right now. EDIT Again: Here's how to edit the boot.ini: [http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/). But I agree, grub is much easier. You can use it for Windows just fine.

As for Ubuntu showing all the installs--yeah, it's annoying. Every time you do a kernel upgrade, it'll run it's Debian Kernel Magic program on your boot file, menu.lst. That will insert any kernels it finds in /boot. You can remove them manually by simply editing your /boot/grub/menu.lst file.

EDIT: Beat me to it. ;)

---

### Post by Herman on 2006-07-14
> Ok for one reason or another I needed to delete the Ubuntu partition of my hd, and expand the NTFS partition letting XP have control over my whole hard drive (for now). Problem being that GRUB screwed up my MBR. Hello. bluezdood, firstly I'm sorry to have to be saying this, but the words "GRUB screwed up my MBR" get me in a bad mood everytime I read them. :twisted:
Normally, they just indicate that someone just doesn't understand GRUB yet though, or how to use GRUB, so I will be patient with you and try to help you anyway.
>   First, it wouldn't load anything since it was already erased, so I reinstall the XP os which is fine, You didn't need to re-install XP, you could have just used your Windows install disk 'Recovery Console to re-write Windows bootloader's first stage to your MBR, overwriting GRUB's first stage. This is all covered on this web-page here, it also explains how to use a Windows 98SE boot disk if for some reason you can't use an 'XP install CD,  [*Click Here.*]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
>  but now I am prompted to choose between two Windows installs, anyone been through this and know how to fix it? I don't know why you would be prompted between two Windows installs, that sounds like a Windows issue, not anything to do with Ubuntu. You can probably fix that by editing boot.ini in Windows. 
> Also, since I had done this before, GRUB shows EVERY installation of Ubuntu, so I ended up with four entries, Ubuntu i386 x2, Ubuntu i686, and Windows XP You can just delete them if they aren't needed, or else comment then out, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#hide_items") to see what I mean.

> Any help or guidance would be appreciated, especially since I plan on installing Kubuntu when I get the chance. Okay, that is good, installing kubuntu will re-install GRUB to MBR for you and will be the fastest and easiest way to fix all your problems. 
Here is my web-page so you can read it and look at the pictures and learn all about GRUB ready for next time. GRUB is the greatest bootloader in the world and we are very lucky to have such a good bootloader. It's just a pity people don't bother learning to use it before they start complaining about it, (sorry, I promised to be kind and patient- I slipped), ](*,) Okay , so here's the link, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm").

---

### Post by bluezdood on 2006-07-15
Well I think you misunderstood me.  I wasn't complaining at all.  It's just a problem and I need to fix it.  If I was complaining, I would've said GRUB sucks! Use Linlo instead!

---

### Post by Herman on 2006-07-15
Okay then, bluezdood, I'm sorry for the misuderstanding, and I apologize. Let's be freinds now. 
I hope those links will be helpful to you, at least.
Best wishes and Regards, :D Herman

---

### Post by bluezdood on 2006-07-16
Hehe, you bet.  Thanks for the links! :)

---

