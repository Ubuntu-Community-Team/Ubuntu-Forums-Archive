---
title: "lubuntu 12.04.3 on dell inspiron 1100 - screen res problem"
date: 2013-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jonny_OGorman on 2013-10-18
hi, i see a lot of people have same problem - live cd everything is ok, install and the screen is 640x480 (the cause is grub loading 640x480 splash which carries on after boot) also found the solution  Edit two files: /boot/grub/menu.lst and /etc/X11/xorg.conf with various setting changes   However my problem is that these two files do not exist!!!!  i found xorg.conf somewhere in /usr/share/... but no sign of menu.lst anywhere -  should i just create this file, why is it missing, what is the full file content and is the xorg.cong file i am editing the correct one to edit, and if so why is it not in /etc/X11?  confused but determined...

---

### Post by Dennis N on 2013-10-18
**menu.lst** is a file that was used in the old grub - not the newer grub2 which is used by 12.04. 

See: 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

to learn more about grub2.

---

### Post by Dennis N on 2013-10-18
For information on xorg.conf and it's replacement, look here:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

### Post by mikewhatever on 2013-10-19
A solution that involves the menu.lst and xorg.conf files would be at least 4 years old, and very probably, irrelevant to any of the currently supported *buntu releases.
Check the Display Settings, more resolutions could be available to switch to.
To change GRUB's resolution, edit **/etc/default/grub**, and change '#GRUB_GFXMODE=640x480' to something like 'GRUB_GFXMODE=1024x768'.

---

### Post by Jonny_OGorman on 2013-10-20
> **mikewhatever said:**
> A solution that involves the menu.lst and xorg.conf files would be at least 4 years old, and very probably, irrelevant to any of the currently supported *buntu releases. Check the Display Settings, more resolutions could be available to switch to. To change GRUB's resolution, edit **/etc/default/grub**, and change '#GRUB_GFXMODE=640x480' to something like 'GRUB_GFXMODE=1024x768'.  
i don't advise doing that change - tried it and ended up with black screen after boot - 
try this instead 
gksudo gedit /etc/default/grub 
change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="vga=773 quiet nosplash" 
save and exit 
sudo update-grub 
gksudo gedit /usr/share/xresprobe/xorg.conf  
after Section InputDevice change the rest of the file into this:  
Section "Device"         
Identifier "Intel 82845G/GL"         
Driver "i810"         
BusID "PCI:0:2:0" 
EndSection  
Section "Monitor"         
Identifier "Internal monitor"         
Option "DPMS"         
HorizSync 28-80         
VertRefresh 43-60 
EndSection  
Section "Monitor"         
Identifier "External Monitor"         
Option "DPMS"         
HorizSync 28-80         
VertRefresh 43-60 
EndSection  
Section "Screen"         
Identifier "Default Screen"         
Device "Intel 82845G/GL"         
Monitor "Internal monitor"         
DefaultDepth 24         
SubSection "Display"                 
Depth 16                 
Modes "1024x768" "800x600" "640x480"         
EndSubSection         
SubSection "Display"                 
Depth 24                 
Modes "1024x768" "800x600" "640x480"         
EndSubSection 
EndSection  
Section "ServerLayout"         
Identifier      "Default Layout"         
Screen          "Default Screen"         
InputDevice     "Synaptics Touchpad" 
EndSection  
save and exit - reboot and cross your fingers  
thanks to this link for direction 
[http://ubuntuforums.org/showthread.php?t=819541&page=2&p=6000430%29:#post6000430%29:](http://ubuntuforums.org/showthread.php?t=819541&page=2&p=6000430%29:#post6000430%29:)

---

