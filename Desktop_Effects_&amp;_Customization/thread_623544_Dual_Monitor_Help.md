---
title: "Dual Monitor Help"
date: 2007-11-26
forum: Desktop Effects &amp; Customization
---

### Post by SilverJester on 2007-11-26
I'm fairly new to linux/ubuntu and never dealt much with dual monitors, My primary monitor is a 22" widescreen lcd monitor (connected with a vga cable to a dvi port on the video card using a vga->dvi adapter). I recently purchased a 50" samsung dlp tv that has a vga port on it (can't afford the dvi/hdmi cables right now unfortunately), I would like to have it connected to play thing like movies and games on the bigger screen. So since the tv will not always be set to receive a signal from the computer, I don't want to have the dual screen mode where the desktop streches across both screens....but I think that mirroring it would be exactly what I need.
I have  nvidia geforce 7600gt, using the generic "nvidia" driver (which seems to work really well for everything so far). So here is my problem...
I keep trying the "screens and graphics" to try and setup the dual monitors but it really doesn't want to work correctly. When I have just LCD connected, it is screen 1...but when I connect the TV, I set screen 2 to it's own resolution yet when I restart X, the TV somehow becomes screen 1 and I cannot get the mirror feature to work even though I have it checked before I restart. Is there a way to manually edit the xorg.conf file to support dual monitors (I'm assuming that is the only  the file that needs editing, as after every attempt I have to manually restore the xorg with a backup I made)?

---

### Post by overdrank on 2007-11-27
> **SilverJester said:**
> I'm fairly new to linux/ubuntu and never dealt much with dual monitors, My primary monitor is a 22" widescreen lcd monitor (connected with a vga cable to a dvi port on the video card using a vga->dvi adapter). I recently purchased a 50" samsung dlp tv that has a vga port on it (can't afford the dvi/hdmi cables right now unfortunately), I would like to have it connected to play thing like movies and games on the bigger screen. So since the tv will not always be set to receive a signal from the computer, I don't want to have the dual screen mode where the desktop streches across both screens....but I think that mirroring it would be exactly what I need.
I have  nvidia geforce 7600gt, using the generic "nvidia" driver (which seems to work really well for everything so far). So here is my problem...
I keep trying the "screens and graphics" to try and setup the dual monitors but it really doesn't want to work correctly. When I have just LCD connected, it is screen 1...but when I connect the TV, I set screen 2 to it's own resolution yet when I restart X, the TV somehow becomes screen 1 and I cannot get the mirror feature to work even though I have it checked before I restart. Is there a way to manually edit the xorg.conf file to support dual monitors (I'm assuming that is the only  the file that needs editing, as after every attempt I have to manually restore the xorg with a backup I made)?

HI have you tried using the nvidia setting to setup twinview. You can use the command ```
gksudo nvidia-settings
``` by using the alt, F2 keys. Hope this helps. good luck!

---

