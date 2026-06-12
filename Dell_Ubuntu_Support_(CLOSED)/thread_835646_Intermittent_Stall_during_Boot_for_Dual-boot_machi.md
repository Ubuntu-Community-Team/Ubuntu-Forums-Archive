---
title: "Intermittent Stall during Boot for Dual-boot machine"
date: 2008-06-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shyuep on 2008-06-20
I am a fairly experienced Ubuntu user (2 years +) but I have been getting this problem that still puzzles me and I can't get my head around it.  I recently bought a new Dell Inspirion 530 and added a second 500Gb Seagate hard drive.  I have Vista installed on the first hard drive (because that's what it came with and I want to keep it for some applications I can't do without) and I installed Ubuntu Hardy Heron on the second hard drive.  As per the default setup, the MBR of the Windows partition is loaded with Grub.

However, when I try to boot into Ubuntu, it sometimes stalls at the loading stage.  So the boot splash screen will basically be stuck at the animated progress bar stage and if I press Ctrl-Alt-F1, the command line output just show 
"Starting ....
Loading..."
and that's it.  Nothing else I do will make the system boot correctly from this stage.  The only way that I solve this problem is to do a Ctrl-Alt-Del and retry the boot and sometimes it works.  This happens around 50% of the time, so I can't even pin point the problem since it is not a definite boot failure.  I am fairly sure that my hard disks are error-free (they are new and I did my own checks).  I have tried reinstalling Ubuntu (twice) and it did not solve the problem.

Any advice on this would be much appreciated. It is not a critical problem since I am able to boot into Ubuntu after I do a Ctrl-Alt-Del, but it is annoying and I am concerned it might herald to some hardware problem that I don't know about.

---

### Post by prinknash on 2008-06-21
This sounds like the quite well-documented problem whereby Hardy won't boot reliably (or at all) on the Inspiron 530 (and other models?) because the SATA setting in the BIOS is set to IDE, the default. Change it to RAID and Ubuntu will boot quite happily. The downside (for people who want to run Windows too) is that XP/Vista won't then boot.

The way round it is to leave SATA set to IDE but to add the instruction all_generic_ide to your menu.lst file. If you google "inspiron 530 sata raid" you'll find plenty of links which explain all this in detail.

p

---

### Post by shyuep on 2008-06-22
Thanks very much for the advice.  Unfortunately I do want to keep Windows (for Photoshop and other applications), so the RAID setting option is out for me.

I have tried the all_generic_ide option but the same problem still persists.  It's frustrating because of the intermittent nature of the problem, so I can't even pinpoint the exact nature of the problem.  From the links you suggested, it seems that if people have this problem at all, the system just simply refuses to boot.  For me, the problem is intermittent, so I am not even sure if it is the same problem.

---

### Post by ariekanarie on 2008-12-01
I am curious if anyone had any progress on this issue. I have a HP DV7-1090 with 2 disks and also installed Vista on disk1 and Ubuntu on Disk 2. I use the standard Vista bootloader on disk1 with the Neogrub bootloader. Sometimes I get 2 progress bars  below each other when I boot Ubuntu and after that laptop stalls on a black screen. Other times the laptop stalls after the Ubuntu progress bar. I noticed that the caps-lock light is blinking when the the booting has stalled. Only remedy is the powering off with the on/off switch. And of course sometimes everything is OK and I get the Ubuntu logon. 

I am experienced in Fedora Core (5+ years) but a novice on Ubuntu. As Ubuntu does not show messages as booting, it is more difficult to investigate this. I'll check the logs to see if I can find some hints. Maybe it is an Nvidia issue? When Ubuntu boots OK, I have no issue with the Nvidia card, but I read about issues when hibernating the laptop.

---

