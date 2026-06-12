---
title: "KDE 4.1, Ibex, Dual Monitors - there's no desktop on the second screen"
date: 2008-11-01
forum: Desktop Environments
---

### Post by eimi on 2008-11-01
Hi,

I've recently installed a Kubuntu 8.10 (clean install). After installation I added nvidia drivers and have rewritten original xorg.conf with nvidia-xconfig to avoid segfault during the parsing of original ubuntu xorg.conf. 

By using the nvidia-settings tool, I set up my display hardware as follows:

Separate X screens (one laptop matrix 1280x800, one external monitor 1680x1050).

This configuration has worked well in KDE 3.5/Hardy Heron. 

Unfortunately, after restarting X-server, the second screen goes online, but without any plasma objects - no desktop, no menu, just blank screen and movable mouse pointer. 

How can I enable support for the second monitor in KDE 4.1?

Thanks for your help.

---

### Post by trawler on 2008-11-08
Just to confirm, I have the same problem exactly.

---

### Post by Uber_Rage on 2008-11-12
I bumped into the same problem and have been able to solve it for myself. The problem occured after I tried to set a custom resolution for the second monitor. I used nvidia-settings to 'auto' set the resolution of the second monitor (both my displays have auto settings) and then restarted Xserver.

Hope this helps !

---

### Post by sloppyc on 2008-11-13
> **eimi said:**
> Hi,

I've recently installed a Kubuntu 8.10 (clean install). After installation I added nvidia drivers and have rewritten original xorg.conf with nvidia-xconfig to avoid segfault during the parsing of original ubuntu xorg.conf. 

By using the nvidia-settings tool, I set up my display hardware as follows:

Separate X screens (one laptop matrix 1280x800, one external monitor 1680x1050).

This configuration has worked well in KDE 3.5/Hardy Heron. 

Unfortunately, after restarting X-server, the second screen goes online, but without any plasma objects - no desktop, no menu, just blank screen and movable mouse pointer. 

How can I enable support for the second monitor in KDE 4.1?

Thanks for your help.
That happened to me when I used Dualview.  I found that Twinview worked better.  I can drag windows to the second screen, and even use the Compiz Cube.  Though it's not without its issues (see my thread).

---

### Post by jstgtpaid on 2008-12-20
I had the same problem.  It was working flawlessly in gnome, but when I tried to go to kde 4.1 I got the same problem.  However, I switch my settings to twinview and everything is working fine now... 

Thanks for the tip, sloppyc!

---

