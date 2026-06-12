---
title: "Compiz and Firefox are devouring my cpu power"
date: 2016-02-14
forum: Desktop Environments
---

### Post by sofasurfer on 2016-02-14
Open terminal and ran "top". Compix and firefox are using 70-90 percent of my cpu. Firefox sometimes hits 127 percent(?).
I went to  help>troubleshooting>start-firefox-in-safe-mode and it seemed to make no difference.

What may be my problem? 

My screens fade of to grey a lot and the system acts like it is frozen for a long time. Sometimes when there is nothing on firefox and no other programs open and the system has been unused for a hour or so, I come back and it is still using 70-90 percent of cpu.

Help?

---

### Post by v3.xx on 2016-02-14
What flavor are you running?

Could it be your computer specs?

```
inxi -b
```

---

### Post by buzzingrobot on 2016-02-14
If you are using any extensions or plugins in Firefox, disable all of them, then close and reopen Firefox. Open a terminal and run top, leaving it open.  Use Firefox for a bit.  If the CPU does not spike, re-enable each extension/plugin one at a time, use Firefox, and watch the CPU.

---

### Post by sofasurfer on 2016-02-14
> **v3.xx said:**
> What flavor are you running?

Could it be your computer specs?

```
inxi -b
```

```
 ~$ inxi -b
System:    Host: daryl-H61M-S2PV Kernel: 3.13.0-77-generic i686 (32 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: MSI model: H61M-P31/W8 (MS-7788) version: 1.0 Bios: American Megatrends version: V3.6 date: 09/29/2013
CPU:       Dual core Intel Pentium CPU G630 (-MCP-) clocked at 2700.00 MHz 
Graphics:  Card: NVIDIA G72 [GeForce 7200 GS / 7300 SE] 
           X.Org: 1.15.1 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1360x768@60.0hz 
           GLX Renderer: Gallium 0.4 on NV46 GLX Version: 2.1 Mesa 10.1.3
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 255.1GB (8.0% used)
Info:      Processes: 177 Uptime: 7:07 Memory: 2058.0/3994.2MB Client: Shell (bash) inxi: 1.9.17 

```

---

### Post by v3.xx on 2016-02-14
I see your running the nouveau driver.

Have you tried any other driver?  It could be the problem.

[http://www.geforce.com/drivers/results/51453](http://www.geforce.com/drivers/results/51453)

Drivers should be available through software-sources>additional drivers.

```
software-properties-gtk
```

You could also run a different desktop that will get you off unity/compiz and put you on metacity for testing.  The "Flashback" desktop will do this.

```
sudo apt-get install --no-install-recommends gnome-session-flashback
```

---

### Post by yoshii on 2016-02-16
I forget what the others are called, but Compiz has a reputation of being resource-hungry compared to the others.

---

### Post by sofasurfer on 2016-02-18
What will happen if I remove compiz without installing a replacement? I have not mess with packages in a long time and I forget what a lot of them do. Is Compiz a total graphics thing or is it only for special graphics? In other words, if I remove it, will I lose important functionallity?

---

### Post by ik-0 on 2016-02-18
a couple of things:
127% isn't a lot if the browser is doing something.  on a 40 core server, I've seen firefox spike to 1000% (10 core equivalents) while it's loading a page.  If there are elements changing on the page (e.g. a gif or javascript), then it's normal to see utilization.

What you are experiencing though is likely due to using software rendering (CPU) vs hardware acceleration (GPU).  As mentioned earlier, it may be your video drivers but you can verify:
$ glxinfo | grep render
should say --> direct rendering: Yes
If it doesn't say direct rendering: yes, then try switching to nvidia's driver.

The other thing is that firefox might not be using hardware acceleration (which can sometimes be a good thing).
Navigate to about:support and it should say GPU Accelerated Windows	1/1 OpenGL (OMTC)
If it doesn't say OpenGL, then navigate to about:config and set [COLOR=#111111][FONT=Consolas]layers.acceleration.force-enabled [/FONT][/COLOR]to True.  Restart your firefox and check about:support again.

---

### Post by yoshii on 2016-02-20
I'm not certain about this type of thing, but I have the impression that you can install a replacement FIRST, and then AFTER verifying that it works, remove set the new default and remove Compiz.  But I haven't tried this myself yet, it's just a hunch.

---

### Post by yoshii on 2016-02-22
I think the window manager of Xfce would be easier on resources. I don't know the exact procedure, but you could possibly install that instead.

---

### Post by goofprog on 2016-02-22
Firefox gets bloated from being online.  Are you using utorrent?  I believe those ad rotators may bloat up the browser in an indirect way.

---

