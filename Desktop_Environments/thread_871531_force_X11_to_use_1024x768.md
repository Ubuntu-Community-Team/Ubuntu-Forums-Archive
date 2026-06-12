---
title: "force X11 to use 1024x768?"
date: 2008-07-27
forum: Desktop Environments
---

### Post by zhimsel on 2008-07-27
Hey guys, I'm having a hard time setting my Xorg resolution. I'm not using a default Ubuntu/Gnome install; I have an Ubuntu-server install with fluxbox/X11 installed myself. Everything works great with the monitor attached (1280x1024-60Hz, autodetected), but I'm going to be removing the monitor and using VNC to use the GUI for the few things I need it for. 

The only problem is, My main PC's resolution is 1440x900, which is shorter than the server's. I'm trying to get X11 to use a 1024x768 resolution instead of 1280x1024, but everything I'm trying is not working. My current xorg.conf is [http://pastebin.com/m1ce75b96](http://pastebin.com/m1ce75b96). I've tried doing the "Display" subsection with the resolution, etc, but it didn't work. Is there something I'm missing?

---

### Post by squaregoldfish on 2008-07-27
I've you're planning to use VNC, you shouldn't need to do anything with your xorg.conf file. You can set up a VNC server with a specific resolution that's independent of X. For example, I have a setup so I can control my main PC from my laptop via tightvncserver. I start the server with:

```
tightvncserver -geometry 1280x800 -depth 24 :1
```

Then, when I connect using the laptop, the virtual screen resolution is correct for the laptop's screen, while the monitor's resolution is unaffected.

Hope this helps,
Steve.

---

### Post by zhimsel on 2008-07-27
> **squaregoldfish said:**
> I've you're planning to use VNC, you shouldn't need to do anything with your xorg.conf file. You can set up a VNC server with a specific resolution that's independent of X. For example, I have a setup so I can control my main PC from my laptop via tightvncserver. I start the server with:```
tightvncserver -geometry 1280x800 -depth 24 :1
```

I actually use x11vnc to tie into my existing X session. The only reason I use X is for Azureus. I have fluxbox start Azureus and x11vnc at startup. SO I need to make the *existing* X session to have a lower resolution.

---

### Post by squaregoldfish on 2008-07-27
There are ways to get the same thing going with tightvncserver, but if you're set on x11vnc then I'll have to leave you in others' capable hands, since my xorg.conf skills are minimal.

Steve.

---

### Post by zhimsel on 2008-07-27
> **squaregoldfish said:**
> There are ways to get the same thing going with tightvncserver, but if you're set on x11vnc then I'll have to leave you in others' capable hands, since my xorg.conf skills are minimal.

Steve.

Actually, I think I just figured out the solution. It's slightly ugly, but it works, and I think I prefer it. I can start x11vnc with the option -scale x/x which will scale the output. I played around and I found that scaling to 9/12 works great. It's still readable, yet fits on the screen.

---

### Post by zekica on 2008-07-27
You can try inserting these lines into Monitor section of xorg.conf:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 20-80
        VertRefresh 60
        Option "PreferredMode" "1024x768"
EndSection
```

---

