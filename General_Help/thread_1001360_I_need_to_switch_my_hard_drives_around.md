---
title: "I need to switch my hard drives around"
date: 2008-12-03
forum: General Help
---

### Post by RFXCasey on 2008-12-03
Ok, here is the deal, I have 2 hard drives. When I started I was planning on making my system dual boot (Ubuntu and XP). One of my HDD is on a Sata2 controller and the other on a regular Sata controller. I wanted the windows install to be faster for games so I figured I would install it on the HDD on the Sata2 controller and put Ubuntu on the regular Sata. I installed Ubuntu as planned but never installed XP and now don't plan to. The problem is I think I am taking a performance hit with Ubuntu on the regular Sata controller. I would like to switch the hard drives around so my Ubuntu in on the Sata2. I think the boot sector or grub or whatever it is is on the Sata2 but Ubuntu itself is on the Sata. My Ubuntu is set up pretty nice and it took me some time to get it that way so I really don't want to reinstall. Is there a way to move the Ubuntu hard drive to the Sata2 controller without messing up my entire system? I was thinking I could just physically plug the Ubuntu drive into the Sata2 and then reconfigure grub but I really don't know enough about that to have confidence that it will work. I have made an image backup of my Ubuntu on the hard drive I was previously going to put XP on using Partimage. I now just plan on using that drive for backups. Could I switch the drives, and then install the backup image or is there an easier way to do it by just editing grub or something similar? If someone could walk me through the process that would be great.

---

### Post by caljohnsmith on 2008-12-03
OK, how about opening a terminal (Applications > Accessories > Terminal) and do the following commands to install Grub to the MBR (Master Boot Record) of your Ubuntu drive:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Then you should be able to plug the Ubuntu drive into your SATA2 controller, make sure your BIOS is still set to boot the SATA2 controller drive, and you should get the Grub menu on start up. How about giving that a shot and let me know how it goes, or if you run into problems. :)

---

