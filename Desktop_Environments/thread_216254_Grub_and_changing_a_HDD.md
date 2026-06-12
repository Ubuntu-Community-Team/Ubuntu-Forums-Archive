---
title: "Grub and changing a HDD"
date: 2006-07-15
forum: Desktop Environments
---

### Post by Aggienator on 2006-07-15
I wonder if someone can help. I have a dual boot XP and Linux with GRUB. Windows and Linux (MEPIS at the moment) are on two separate physical drives. I want to remove the drive that has Linux on and put in a new one, to dual boot with Ubuntu.

My problem is that when I remove the old Linux drive and try to boot I get a screen ful of "01". I presume this is because GRUB is looking for something on the drive I have removed. Can anyone tell me how to reconfigure GRUB so I can boot without the old drive?

Thanks

---

### Post by krazykirk on 2006-07-15
You can reinstall grub (just grub) from a live cd!

And [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)  tells you how!

---

### Post by Herman on 2006-07-15
Aggienator, The easiest thing to do would be to download GAG Boot Manager, (which is free, and only a small download), and make a GAG Boot Manager CD or floppy disk to boot with until you are ready to install Ubuntu. It is a good idea to have a GAG disk anyway. A GAG Boot Manager floppy would be the better than a CD, if you have a floppy disk drive. Otherwise a CD will do. 
Then when you install Ubuntu, Ubuntu's GRUB will overwrite Mepis's GRUB on your MBR, and things will be fine. [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm") for GAG Link.

I don't think re-installing GRUB will work because with your Linux disk removed, the MBR will be pointing into empty space. Linux GRUB can't be installed in Windows. You can get GRUB for Windows. I have not looked into that, but I know it exists.
Regards, Herman :D

---

### Post by Aggienator on 2006-07-16
Thanks Herman, this has solved my problem :-)

The Ubuntu forums come to the rescue again! I think one of the main reasons I am converting to Ubuntu and one of the distro's greatest strengths is this forum.

Thanks Again, Aggie

---

