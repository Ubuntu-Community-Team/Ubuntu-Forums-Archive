---
title: "cannot eject cdrom"
date: 2006-02-05
forum: Desktop Environments
---

### Post by gormine on 2006-02-05
It's telling me the program needs to be installed SUID root.

---

### Post by madmetal on 2006-02-05
try right click on the cd icon and click on eject.
or install automatix wich features cdrom eject from cdrom button.

---

### Post by gormine on 2006-02-05
[QUOTE=madmetal]try right click on the cd icon and click on eject.
or install automatix wich features cdrom eject from cdrom button.[/QUOTE]


I am getting the error when I right-click and select eject. I have automatix installed with the eject cdrom by button feature working correctly. This just bugs me.

---

### Post by steve.horsley on 2006-02-05
What error?

My guess is that it says the drive is in use. Do you have a console window open that is "in" that drive? Also, I have sometimes had to close all instances of konqueror before I can eject or unmount CDs.

---

### Post by gormine on 2006-02-05
[QUOTE=steve.horsley]What error?

My guess is that it says the drive is in use. Do you have a console window open that is "in" that drive? Also, I have sometimes had to close all instances of konqueror before I can eject or unmount CDs.[/QUOTE]


With all programs closed, it still gives the "eject error" Error: this program needs to be installed suid root
eject: unmount of `/media/cdrom0' failed

---

### Post by Breaks on 2006-02-05
Have you tried unmounting the drive by command manually then ejecting?

---

### Post by gormine on 2006-02-05
[QUOTE=Breaks]Have you tried unmounting the drive by command manually then ejecting?[/QUOTE]


I've tried both umount and eject. If I don't use sudo, eject tells me that it needs to be installed suid root. umount works as well as sudo eject.

sudo chown root /usr/lib/eject had no effect on eject working.

---

### Post by vruum on 2006-02-05
maybe ```
sudo dpkg-reconfigure eject
``` will give you the option to install suid root, I'm not sure, but it might.

---

### Post by gormine on 2006-02-05
[QUOTE=vruum]maybe ```
sudo dpkg-reconfigure eject
``` will give you the option to install suid root, I'm not sure, but it might.[/QUOTE]


This did not give me any options or help at all. I tried uninstalling the package and reinstalling with no luck.

---

### Post by kingsidy on 2006-02-05
reboot, or do a hard reboot and take the cd out. also usually you need to umount the cd drive before it  could eject. you can also use the disk mounter applet which does that automatically.

---

