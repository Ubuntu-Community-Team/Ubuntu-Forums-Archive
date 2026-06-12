---
title: "My X get restarted automatically"
date: 2007-11-15
forum: Desktop Environments
---

### Post by sathyz on 2007-11-15
I have installed Ubuntu 7.10. I have been logged out of my X automatically. Please fine the attached log file and let me know what to do?

skumar@skumar-laptop:~$ tail -n 50 /var/log/Xorg.0.log| less
skumar@skumar-laptop:~$ tail -n 50 /var/log/Xorg.0.log
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x768" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x800" (width too large for virtual size)
(II) intel(0): Not using default mode "1152x768" (width too large for virtual size)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV

---

### Post by solar george on 2007-11-15
You haven't attached the log file.

Do you mean that you get the login screen, you login and then it throws you out or do you not even get that far.

---

### Post by sathyz on 2007-11-15
I could login.. work.. after few min or hours, I am thrown back to gdm login.. closing all my works/windows.

---

### Post by sathyz on 2007-11-15
The tail of log when my  X restarted last time:

skumar@skumar-laptop:~$ head -n 890 /var/log/Xorg.0.log | tail 
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TV disconnected
(II) intel(0): EDID for output TV
Synaptics DeviceOff called
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4

---

### Post by solar george on 2007-11-15
Well from here its all guesswork,

Try logging in to a failsafe gnome session and see if that works.

Try changing the monitor setting in the Screens and Graphics config (hint: get it to try and auto detect your monitor)

---

### Post by sathyz on 2007-11-16
I did auto-detect ( did a dpkg-reconfigure xserver-xorg ). let me see any issues after this.

---

### Post by sathyz on 2007-11-18
I am facing this one i run into battery power mode. No such problem when i am running on AC Power. but Once i switch back to AC power mode from battery mode then i am facing this problem

---

