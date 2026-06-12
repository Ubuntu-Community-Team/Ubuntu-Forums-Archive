---
title: "Computer goes strait to Vista and won't show grub, no matter what!"
date: 2009-01-07
forum: General Help
---

### Post by Maxxtsch on 2009-01-07
Grub will only show if I have to open up the computer case and unplug the SATA cable from the drive with vista. How do I get grub to show up first so that it shows both OS's like it did. But I can't have then both plugged, or it goes strait to vista.:confused:


***
Note, I had a dual boot, just like I wanted it, from 2 drives(Vista and Ubuntu). I had to reformat both drives, reinstall Vista and Ubuntu (8.10). I did Vista first. Then Ubuntu, and I already spent like a day messin' with the BIOS, it's not that.

---

### Post by Maxxtsch on 2009-01-07
Bump

---

### Post by Maxxtsch on 2009-01-07
Bump *ok some one help me*

---

### Post by sPiN1 on 2009-01-07
i get this problem when installing windows after ubuntu, are you sure you didn't install it after? the only simple way i've found of fixing it is installing ubuntu second. if you have no important information and a little time on your hands installing ubuntu again with a fresh grub should do the trick

---

### Post by Maxxtsch on 2009-01-07
shouldn't there just be a grub command, or a fix?

---

### Post by sPiN1 on 2009-01-07
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

check these

---

### Post by 3pinner on 2009-01-07
I have a similar setup with Ubuntu on one drive Windows 2000 on another.
I made sure my Ubuntu drive was the master, Windows the slave, before installig Ubuntu.
Whether that would make a difference in your case I really can't say, but it seems like GRUB was loaded when you installed Ubuntu.

---

### Post by 2hot6ft2 on 2009-01-07
If there are only the 2 drives there are 2 options that come to mind. Switching the tapes where they connect to the mother board. That would assume that the grub is on the drive that is being seen second and windows is on the drive being seen first.

Second is reinstall grub.

To restore Grub to your MBR, so if you boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

And that's all it should take.

---

