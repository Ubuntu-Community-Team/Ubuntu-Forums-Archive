---
title: "Wubi to full instal"
date: 2008-12-23
forum: General Help
---

### Post by Feivel on 2008-12-23
I have been using Ubuntu for just over 1 1/2 years. I tried it out on a live CD and installed it via Wubi about 1 hour later. I have not used Vista since I put Ubuntu on. I have XP and Wubi on my laptop and I will keep XP there. What I want to do is change my Wubi install to a full install of Ubuntu so I can rid myself of that virus/worm known as Microsoft Windows.  I am not looking forward to using gparted and LVPM (I do have both) but what I really want to do is backup my Wubi install (config, package list, etc.), do a fresh install from a new 8.4 live CD and then reinstall from the package list I made then copy over my config. I know it's a tall order but can some of you guys lend a hand p

---

### Post by azmo35 on 2008-12-24
well why not do backup and then transferred your wubi to a real Partition if you are not satisfied you can use the backup.You are talking about "virus/worm known as Microsoft Windows" gparted and LVPM thei are free of virus/worm Linux thing,use live cd for gparted easy as 1 or 2 clicks and lvpm takes the time off a coffee are you afraid of Linux virus/worm.

---

### Post by Feivel on 2008-12-24
> **azmo35 said:**
> well why not do backup and then transferred your wubi to a real Partition if you are not satisfied you can use the backup.You are talking about "virus/worm known as Microsoft Windows" gparted and LVPM thei are free of virus/worm Linux thing,use live cd for gparted easy as 1 or 2 clicks and lvpm takes the time off a coffee are you afraid of Linux virus/worm.

Just figured a fresh install would be better than a transfer through LVPM and an install from the live CD would totally avoid booting into windows (which I have no desire to do considering how long bootup takes).

ETA - Installing fresh removes the necessity of creating partitions through gparted since I intend to overwrite Windows anyway.

---

### Post by azmo35 on 2008-12-24
The question is dual boot or single boot? 
Answer dual boot ubuntu is the first and you can change your menu.lst to not display the 10 sec of default menu to 0 sec this way you not see windows,single boot after the lvpm transfer use gparted delete windows partition and use the free space for ubuntu,very easy no Linux virus/worm.

---

### Post by Feivel on 2008-12-24
> **azmo35 said:**
> The question is dual boot or single boot? 
Answer dual boot ubuntu is the first and you can change your menu.lst to not display the 10 sec of default menu to 0 sec this way you not see windows,single boot after the lvpm transfer use gparted delete windows partition and use the free space for ubuntu,very easy no Linux virus/worm.

Yes, I understand how to transfer with LVPM and the need to create partitions in gparted but that is not what I am asking. I have a list of my installed software from ```
dpkg --get-selections > installed-software
``` and I need to backup my program configuration files (maybe it would be cleaner not to backup my configuration) (guess they are in my home directory) and my email. Then I can do a fresh install from a LiveCD and run ```
dpkg --set-selections < installed-software
``` to reinstall all my software then reinstall all my configuration files. No gparted necessary since I want Ubuntu ONLY.

---

### Post by azmo35 on 2008-12-24
I understand you want all your software and setings so lvpm will do that for you well it did on my old crapy laptop.

---

### Post by Feivel on 2008-12-24
> **azmo35 said:**
> I understand you want all your software and setings so lvpm will do that for you well it did on my old crapy laptop.I undersatnd it would but using LVPM requires making 2 extra partitions with gparted than a boot into Windows to uninstall Wubi. I just figured it would be easier to install fresh from a LiveCD with an installed list of packages and backups of certain configs from my home directory (no gparted, LVPM or boot into Windows required).

---

### Post by azmo35 on 2008-12-25
Right, good luck change the title of you thread how to copy my wubi settings and them copy to a fresh install,thanks.:(

---

### Post by Jammanuser on 2008-12-28
> **Feivel said:**
> I undersatnd it would but using LVPM requires making 2 extra partitions with gparted than a boot into Windows to uninstall Wubi. I just figured it would be easier to install fresh from a LiveCD with an installed list of packages and backups of certain configs from my home directory (no gparted, LVPM or boot into Windows required).

I just recently used LVPM myself, and it worked fine, just FYI! :) I'm not sure why you're so against partitioning your hard drive...;) Its fairly easy, and doesn't require too much technical know-how! :P If the reason you don't want to use it is because of the time factor...then my answer would be that it would take just about the same amount of time to install it with the LiveCD, and to then install the list of packages.

BTW, the LiveCD should already have Gparted on it, so you wouldn't have to download it, and create another CD...simply use your existing LiveCD! :lolflag:

Of course, it is entirely your choice though...

BOL.

-Jam man

:guitar:

EDIT: And of course there's always the added advantage using LVPM, by being able to dual boot...which would not be the case if you did it the other way. Cheers! :D

---

### Post by Kingy_0 on 2008-12-29
Hello, I'm contemplating of turning my Wubi installation into a fully usuable OS (seperate from Windows) what sort of steps do I need to take to do this?

I know I need to partition my HDD to do this, but what about copying the vhd of xubuntu, the file stored on my Windows OS?

Is there a simple guide anywhere online, that you may know of I can follow?

ps. Apologies if I'm stealing your thread!

---

### Post by Jammanuser on 2008-12-30
> **Kingy_0 said:**
> Hello, I'm contemplating of turning my Wubi installation into a fully usuable OS (seperate from Windows) what sort of steps do I need to take to do this?

I know I need to partition my HDD to do this, but what about copying the vhd of xubuntu, the file stored on my Windows OS?

Is there a simple guide anywhere online, that you may know of I can follow?

ps. Apologies if I'm stealing your thread!

Like I was telling the above user, you can use LVPM to transfer your Wubi install to a partition, and you can create the partition with Gparted, which will already be on your LiveCD, if you have one.

Hope this helps! :)

-Jam man

:guitar:

EDIT: Here's the link to the LVPM transfer tutorial, where you can obtain much more information on the program: [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

EDIT #2: And here is a link to a screenshot-based guide on resizing partitions with Gparted: [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by Kingy_0 on 2008-12-30
Thanks, that's really appreciated. It's just I'm enjoying using Ubuntu a lot more than XP, but I still need to use it for the time being. 
Until I find an open source alternative for MS Groove 2007.

So dual-booting seemed ideal option. I'll be sure to follow the instructions you kindly posted, and thanks again!
:D

---

### Post by LRTIMKEN on 2008-12-30
Content's nice and I support you![SKF](http://www.nskcn.com/product/ShowClass.asp?ClassID=27) [skf](http://www.nskcn.com/product/ShowClass.asp?ClassID=27) [SKF](http://www.9skf.cn/product/ShowClass.asp?ClassID=27) [skf](http://www.9skf.cn/product/ShowClass.asp?ClassID=27)

---

### Post by creek23 on 2008-12-30
> **Kingy_0 said:**
> ...I still need to use it for the time being. 
Until I find an open source alternative for MS Groove 2007.I think you can try [Collaber]("http://www.collaber.com/"). ;)

---

### Post by DJ_Barney on 2009-01-02
> **Feivel said:**
> I undersatnd it would but using LVPM requires making 2 extra partitions with gparted than a boot into Windows to uninstall Wubi. I just figured it would be easier to install fresh from a LiveCD with an installed list of packages and backups of certain configs from my home directory (no gparted, LVPM or boot into Windows required).

A fresh install from CD will automatically go through the various stages, but you still have to make the same decisions about partitioning as you do by following the LVPM procedure. If you really want to do it your way then read the apt-get man page for a possible imported package list solution. Copying ".settingfile" configs from the home directory should work in most circumstances.

---

