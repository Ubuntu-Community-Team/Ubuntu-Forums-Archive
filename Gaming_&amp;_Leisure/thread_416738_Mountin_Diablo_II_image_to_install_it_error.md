---
title: "Mountin Diablo II image to install it error"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by thesonork on 2007-04-21
Hey guys... i got a strange error here... 

Im running Feisty, and my wine is on wine-0.9.35
I got installed wow and working with wine so everything works fine with that.
I just wanted to install my Diablo II again, which i lost cuz i had to format my drive. the porblem now is that when i mount the install disc iso using 
```
sudo mount -o loop /d2install.iso /media/cdrom
```
I got even the icon on the desktop and everything is fine... i open the install.exe and enter my cdkey and stuff and start the install.... the window with the to bars comes but nothing installs and it jsut hangs up random time and nothing happens....
so i killed my wine process and wanted to unmount my cddrive but! it tells me that 
```
Umount error
/dev/loop not mounted
unmount failed
```
How can this be?!
I see the drive as working but cannot umount it cuz its "not mounted" well could this cause my install to fail?!
(well it worked on dapper drake)

thanks for helping

//sonork

---

### Post by lakersforce on 2007-04-21
What command did you use to unmount?

---

### Post by thesonork on 2007-04-22
I tried unmounting via rightclick and ```
umount /media/iso
``` both tells me no loop  mounted :-\

---

### Post by lakersforce on 2007-04-22
Be sure to use SUDO.

If you for example mounted it with:

```
sudo mount -o loop diablo2.iso /media/cdimage
```

use the following command to unmount:

```
sudo umount /media/cdimage
```

---

### Post by thesonork on 2007-04-22
well the umounting inst the problem actually and i got it to unmount but still tells me when i install stuff that my loop's not mounted... is there any command to see if my loop device working properly?

---

