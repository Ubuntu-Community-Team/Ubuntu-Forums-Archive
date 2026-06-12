---
title: "(noobie) How to force screen mode with monitor unplugged at bootup?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by stevech on 2006-08-26
My Goal: 
Ubuntu on PC with PCI Bus ATI 9200 Graphics card, no monitor; using VNC.

With monitor unplugged at boot-up, Ubuntu's drivers choose 640x480 rather than the resolution I chose as default. Something to do with drivers thinking the absence of a connected VGA monitor must mean go to TV out resolution.

How can I force desired screen res without monitor plugged in at bootup?

---

### Post by infoseeker on 2006-08-26
I am not sure if this will work but why dont you try editing the /etc/X11/xorg.conf file of any resolution other than the one you need (hash them out) and see what happens.

---

### Post by steve.horsley on 2006-08-26
IT defaults to a safe 640x480 resolution if it can't get the monitor frequencies. If you give it the monitor frequencies in the xorg.conf file, that should keep it happy. You need to find the monitor section and provide HorizSync and VertRefresh values. Below is a sample from my PC. You should use the corect values for your monitor.

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-70
        VertRefresh     43-60
EndSection

```

---

### Post by stevech on 2006-08-26
where would that file be?

And what are the units, below: HorizSync - in KHz? Vert refresh in Hz? With the wide range shown below, looks like it doesn't matter much.



Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-70
        VertRefresh     43-60
EndSection

---

### Post by stevech on 2006-08-27
thanks. That fixed it. (I kept the monitor's name as L17).

Next issue is that when I run Ultra-VNC from my windows XP machine to the Ubuntu machine, my XP machine's CPU Usage goes to 100%. This does not happen when that XP machine UVNC's to two other machines, but they run the same UltraVNC as does XP. The VNC on ubunto is different.

I can't deal with 100% utilization. 
I did try changing the ubuntu machines screen resolution. But the GUI does not allow me to change the bits/pixel, nor does it even show me what it is using. 

So far I've found ubuntu to be a hassle and goofy as compared to Xandros and SUSE which just worked right the first time.

Other problems I didn't have with these other Distros include WiFi doesn't work (says "connected" with WEP but it really isn't), has no WPA, no signal strength display). Printing with HP5510 no workie, and so on.  I'm about to bail on ubuntu; it seems written to run in a super bare bones mode for folks with a $300 PC.

---

