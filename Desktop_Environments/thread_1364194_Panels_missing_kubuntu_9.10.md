---
title: "Panels missing kubuntu 9.10"
date: 2009-12-25
forum: Desktop Environments
---

### Post by newbie2010 on 2009-12-25
Hi, I am completely new to Linux. I have installed Kubuntu 9.10 recently and edited /etc/fstab file for automatic loading of windows vista partition on start up. On restarting the system, I find windows partition disk loaded but I find both the top and bottom panels, missing!! Also  Right clicking  on ' desktop-> Applications -> settings -> panel ' does not work. Please help!! 

The contents of my fstab file now is ...

proc            /proc           proc    defaults        0       0
UUID=bc761081-6e50-4e48-942f-41c2cf7f6db3 /               ext3    relatime,errors=remount-ro 0       1
UUID=751f3bcc-f897-40c1-9502-3563db021871 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sta1       /mnt/windows    ntfs default 0 0

---

### Post by gunksta on 2009-12-25
Interesting. Potentially, these are unrelated problems.

Try changing "default" to "defaults"

Conversely you could temporarily comment this line out and see if plasma starts to work again.

Question - When you load up your desktop, do you still have a background image?

---

### Post by newbie2010 on 2009-12-26
Yes, I have my desktop background.I have also changed default to defaults, but it still has no effect...I find my panels to be missing still!! :(

---

### Post by gunksta on 2009-12-26
Well this certainly qualifies for odd. It is possible that the disk changes are a red-herring and not the actual cause.

It's possible that Kubuntu has gotten confused regarding the dimensions of your desktop. I use a laptop @ work connected to a large LCD screen. Because the LCD screen is wide-screen format and the laptop screen is not, the system sometimes gets a little confused and I have to set my resolution manually.

Hit Alt + F2 to pull up the run dialog and type in sys. One of your options will be System Settings. Run the Systems Settings tool. Go to Display (bottom section) and make sure your screen resolution matches your monitor's specs. For example - right now this laptop is running @ 1400 x 1050, which is a little high-res, but OK. But, if it were running at 1400 x 1280, the bottom panel would be off-screen and thus appear to be "hidden".

Failing that - We could try to add a new panel to your desktop. Anywhere on the KDE Desktop, right click on the desktop and try to add a new panel. Note, you will need to add widgets to the otherwise plain panel to get something at all useful.

Another option would be to just nuke your plasma settings and restore the defaults. Open konsole and run this:
```
rm ~/.kde/share/config/plas*
```

---

### Post by newbie2010 on 2009-12-26
Its really strange!!! I have checked the resolutions and both seem to be 1680*1050....I have tried the command in Konsole window still no change!! Meanwhile I tried the command gnome-panel...and I get both the panels at the top and bottom, again its really strange that I am not able to boot...when I do a hard-boot and restart the panels disappear again!!! Seems that i will have to re-install Ubuntu 9.10 completely :(

---

### Post by gunksta on 2009-12-28
Perhaps we need more info -- because yes, this is sounding a little strange.

From a konsole window try this.

killall plasma-desktop && plasma-desktop

Do you get any errors?

---

