---
title: "Getting a Dell Inspiron w/ Ubuntu"
date: 2008-06-16
forum: Desktop Environments
---

### Post by VGF on 2008-06-16
I ordered it a week ago, and it should be here tomorrow.  The Inspiron Ubuntu line comes with 7.10 preinstalled.  Is there any reason I shouldn't upgrade to 8.04 right away?  Or is it best just to do it as soon as possible to get it out of the way?

---

### Post by Fingers &amp; Thumbs on 2008-06-16
This really depends on what you want from the operating system. I use a Dell Inspiron 9300, it wasn't shipped with Ubuntu installed, I made the change myself when Fiesty was the most up to date version. I am currently running it as a dual boot, using Ubuntustudio 8.04 and ubuntu 7.10. My reason for this is basically that I haven't managed to get everything running on 8.04 yet, and it is clear from reading that the community in general hasn't got all of the answers yet. But keeping it installed allowes me to keep trying, keep it updated, and sooner or later it will be fine and I can remove 7.10.
  Nothing major, just little things, the most important to me being my huawei e220 mobile modem, works a treat with 7.10 but not with 8.04.
  The only way for you to really be sure would be to dual boot in the same way, If you find 8.04 does everything you need, you can easily discard 7.10

---

### Post by danbodoh on 2008-06-16
I'd go right to 8.04, and make sure to get the latest (-19) kernel that appear today in hardy-updates.  Suspend/Resume will work much better; I had lots of trouble in 7.10 (Gutsy).

I've set up two Inspiron 1525's with Ubuntu in the last few months, and they are both running great on 8.04.

Check this page out for a few pointers about upgrading Dells to 8.04: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

Dan Bodoh

---

### Post by Aearenda on 2008-06-16
I have an Inspiron 530 (originally with Windows). I would upgrade, but beware of the problem some Inspirons have with the Hardy kernel. You either have to add the all_generic_ide kernel parameter to the parameters as you boot, or change the BIOS SATA mode to 'RAID'. Doing the latter is dead easy, and since you won't be dual-booting Windows has no side-effects.
I have heard that a recent BIOS update fixes this issue, but I haven't tried it.
Instructions on the settings are at [http://ubuntuforums.org/showpost.php?p=4799028&postcount=15](http://ubuntuforums.org/showpost.php?p=4799028&postcount=15).

---

### Post by lelmo85 on 2008-07-05
I want to thank you and the other people who pointed the way to 
all_generic_ide. I installed Fedora 9 with no problem, let it automatically install grub for Ubuntu, Fedora, XP, 98, old DOS, new DOS. I added all_generic_ide to the kernel line on the splash screen, but had to sudo to menu.lst in /boot/grub and make change there as follows: kernel (hd0,2)/boot/vmlinuz-2.6.22-14-generic >****  root=UUID=(hex numbers-no()) splash ro quiet> all_generic_ide so it would add on in splash screen
I have a home-made desktop with a WD74 sata drive and an IBM SCSI drive. (What a mess, huh?) Thanks again. Les

---

