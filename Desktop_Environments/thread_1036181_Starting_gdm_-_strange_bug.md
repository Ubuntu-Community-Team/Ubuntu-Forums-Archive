---
title: "Starting gdm - strange bug"
date: 2009-01-10
forum: Desktop Environments
---

### Post by Rahzizzle on 2009-01-10
Ok, so I had Hardy Heron installed and it worked perfectly up until I installed Vista as a dual boot option. Now when I select ubuntu in the grub bootloader it takes me to the login screen and when I enter my username and password it makes the login noise but the only thing on the screen is the mouse cursor.

I have tried the recovery option and tried doing dpkg-reconfigure also, what I want to know is when I hit ctrl + alt + F3 and get taken to the terminal and type "/etc/init.d/gdm start"

it says "starting gdm"  <ok>

and that's it... what else do I have to type to load the gdm or what else should I try to get this working??

:confused::confused::confused:

---

### Post by mgol on 2009-01-10
gdm screen is available by pressing [Ctrl]+[Alt]+[F7]. To restart (it might be already started), type:
```
sudo /etc/init.d/gdm restart
```.

---

### Post by Ptero-4 on 2009-01-10
Try updating your packages. Maybe a new version fixes the strange behavior in gdm. Also try to install another windowmanager and select it from gdm to see if it´s an issue with your GNOME (GNOME tends to stop loading if the system clock is set to a date way behind or ahead the correct date), if the windowmanager opens properly, try and open the time & date control panel and set the time and date properly if needed. If that doesn´t fix your problem, go to your windows OS and install ext2ifs in it, then open your linux partition and delete the GNOME and gdm config files, and boot back to linux to see if GNOME loads.

---

