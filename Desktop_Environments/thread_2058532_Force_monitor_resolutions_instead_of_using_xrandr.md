---
title: "Force monitor resolutions instead of using xrandr?"
date: 2012-09-15
forum: Desktop Environments
---

### Post by uga_boy on 2012-09-15
Is there anyway to manually set the monitor supported resolutions and make them permanent? I'm using xbutunu on a legacy system and running vga to the pc input on my rear projection Samsung DLP TV. The live cd runs the optimum resolution on the first go but after an installation the refresh rates keep getting messed up. The tv doesn't support any refresh rate above 60 and every time I reboot it I immediately get 'Unsupported PC resolution' from my tv, unable to see the desktop because it resets the refresh rate to 61. If I start the OS using the grub menu and add 'nomodeset' to the end of the load line, I can see it again, but it's using a VESA driver and is extremely choppy. Using xrandr -q from the terminal displays 3 resolutions supported, all of them incorrect. 
 
This problem also occurred with XBMCubuntu but I was able to rectify it by modifiying the ui_settings.xml (or something similar) found in my homedir/.xbmc folder. Is there a similar file for the DWM? or X11? Can I force a resolution through the grub command?
 
Any help would be greatly appreciated.

---

### Post by Epodx64 on 2012-09-15
you can force the video from grub depending on what kind of video card you have if it's an intergrated Intel video card from grub just add 

video=1280x1024-24@60

and if that doesn't work you can try 

video=VGA-1:1280x1024-24@60

I don't know how to do it on Nvidia cards if you need the ATI instructions post back with the type of Ati card you have and ill tell you how to do it.

---

### Post by uga_boy on 2012-09-16
Thanks for the response. 
 
It's an onboard Intel chipset. Going now to give it a try.

---

### Post by uga_boy on 2012-09-16
That did it! Thanks!

---

### Post by Epodx64 on 2012-09-16
> **uga_boy said:**
> That did it! Thanks!
No problem I'm glad it worked for you.

---

