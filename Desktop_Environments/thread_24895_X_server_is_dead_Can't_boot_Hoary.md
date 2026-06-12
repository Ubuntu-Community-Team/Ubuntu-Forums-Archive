---
title: "X server is dead? Can't boot Hoary"
date: 2005-04-08
forum: Desktop Environments
---

### Post by coldturkey on 2005-04-08
I followed [this](http://www.ubuntuforums.org/showthread.php?t=20769) in every step but when I restarted (ctrl+alt+backspace) Ubuntu didn't boot. Instead I got Some error messages from xorg.conf. X-Serv and my desktop won't boot, i cant acsess xorg.conf from the "none-grafic-mode".
Is there a way out or do i need to format and install everything again :/?

---

### Post by alastair on 2005-04-08
Just log in on a text console (CTRL+ALT+F2, say) then :

cd /etc/X11

Then - assuming you backed up the xorg.conf file before editing - copy your backup file over the real one.

If you made no backup - you will have to edit the xorg.conf file and undo your changes.

To get back to GDM/login :

sudo /etc/init.d/gdm restart

---

### Post by alastair on 2005-04-08
Or - perhaps - 

cd /etc/X11
sudo mv xorg.conf xorg.conf.comp
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

---

### Post by coldturkey on 2005-04-08
Thanks alot alastair! It works fine now :)
One thing im missing tho is the scroll wheel on my MX510, it doesnt work /

---

### Post by c_dog on 2005-04-09
[QUOTE=coldturkey]Thanks alot alastair! It works fine now :)
One thing im missing tho is the scroll wheel on my MX510, it doesnt work /[/QUOTE]

You need to set up more than the default 5 mouse buttons in xorg.conf
```
Section "InputDevice"
   Identifier  "Mouse1"
   Driver      "mouse"
   Option "Protocol"     "ExplorerPS/2"
   Option "Device"       "/dev/mouse" # If you are using a USB mouse then give "/dev/input/mice"
   Option "Buttons"      "7"          # adding this enables the extra buttons on the MX700
   Option "ZAxisMapping" "6 7"        # adding this maps wheel scrolling events to mouse buttons 6 & 7
EndSection
```

---

### Post by daniels on 2005-04-09
If dpkg-reconfigure xserver-xorg ever overwrites your configuration, it will make a backup itself and tell you where (as /etc/X11/xorg.conf.yyyymmddhhmm).

---

