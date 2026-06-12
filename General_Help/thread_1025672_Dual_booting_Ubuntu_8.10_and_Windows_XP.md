---
title: "Dual booting Ubuntu 8.10 and Windows XP"
date: 2008-12-30
forum: General Help
---

### Post by Zyndrof on 2008-12-30
Hi,

For the first time since I installed Ubuntu 8.04 I actually want - or rather need - Windows XP for a couple of applications.

So I used a guide to install XP on a separate partition (called "L:/").

It took me less than 2 minutes to understand why I left XP in the first place.

Naturally, none of the installed drivers worked and I had to download them in Ubuntu and place them on a separate drive. When attempting to install them though... they won't unless the partition's name is "C:/". That name is occupied by my file drive... Where I keep files and folders that are not related to any applications.

I'm guessing the easiest way to make it work properly would be to reformat the hard drive and install XP. Then create a partition for Ubuntu and make Ubuntu the main system.

Is there a better way? The guide discouraged users from renaming the drives.

Thank you,
Zyndrof

---

### Post by Hydrid on 2008-12-30
Yes you are right!The best way to Ubuntu to work fine is to install 1st Windows and after Ubuntu!

---

### Post by masque7 on 2008-12-30
> **Zyndrof said:**
> Hi,

For the first time since I installed Ubuntu 8.04 I actually want - or rather need - Windows XP for a couple of applications.

So I used a guide to install XP on a separate partition (called "L:/").

It took me less than 2 minutes to understand why I left XP in the first place.

Naturally, none of the installed drivers worked and I had to download them in Ubuntu and place them on a separate drive. When attempting to install them though... they won't unless the partition's name is "C:/". That name is occupied by my file drive... Where I keep files and folders that are not related to any applications.

I'm guessing the easiest way to make it work properly would be to reformat the hard drive and install XP. Then create a partition for Ubuntu and make Ubuntu the main system.

Is there a better way? The guide discouraged users from renaming the drives.

Thank you,
Zyndrof
It is *easier* to dual-boot with Windows being installed first. With Linux installed first, Windows overwrites GRUB.

However, it can be done. Just back up GRUB's configuration file and follow this guide: [Install Linux and XP, with Linux installed first](http://apcmag.com/how_to_dualboot_vista_with_xp__stepbystep_guide_with_screenshots.htm)

---

### Post by mojoman on 2008-12-30
> **Zyndrof said:**
> Is there a better way?

The best way is to ditch XP ;)

---

### Post by Zyndrof on 2008-12-31
> **mojoman said:**
> The best way is to ditch XP ;)

Which is exactly what I have done for several months ;) Some apps just doesn't work under WINE though.



The guide that was posted earlier is the one I used. Both Ubuntu and XP works and boots... But XP is worthless since I cannot install any drivers for sound, graphics or network.

---

### Post by masque7 on 2008-12-31
> **Zyndrof said:**
> Which is exactly what I have done for several months ;) Some apps just doesn't work under WINE though.



The guide that was posted earlier is the one I used. Both Ubuntu and XP works and boots... But XP is worthless since I cannot install any drivers for sound, graphics or network.
Basically you're saying that the drivers won't install because they keep installing to your C: drive, which isn't your Windows installation?

Surely there's an *advanced installation* option with these drivers that actually lets you select which directory/drive to install them to?

---

### Post by Zyndrof on 2009-01-01
> **masque7 said:**
> Basically you're saying that the drivers won't install because they keep installing to your C: drive, which isn't your Windows installation?

Surely there's an *advanced installation* option with these drivers that actually lets you select which directory/drive to install them to?

No, there isn't. And that is plain weird...

---

