---
title: "Slow selection after I've loaded any application"
date: 2009-10-03
forum: Desktop Environments
---

### Post by Young Druid on 2009-10-03
Hi. I installed Xubuntu 9.04. My PC is quite old: GeForce4 MX 440, Pentium 4 3.06 GHz.
So I have a problem and I couldn't determine the source of it.
1. Xfce is just loaded.
2. Make selection by mouse on desktop and move it quickly. Everything is fine.
3. Open any application (Opera, Pidgin).
4. Make selection by mouse on desktop and move it quickly. Selection is very slow. It looks like my PC is veery old.

Could anybody suggest what's the reason of such behavior?
Thanks.

P.S. I also installed LXDE. The same problem. After booting the system selection is OK. When I open any application, selection is slow.

---

### Post by kerry_s on 2009-10-03
how much ram?
that is not old, i'm running on 450mhz 256mb ram, 3.06 GHz would be fantastic. :lolflag:

---

### Post by Young Druid on 2009-10-03
1 Gb. 
Yep. I read some articles about slowness of Xubuntu. All of those configurations were worse than mine. :) But all the same I want to determine the reason. It's very strange for me. Selections begin to be slow even after I've started Thunar.

---

### Post by kerry_s on 2009-10-03
i would guess your not using the right vid driver or it's not setup correctly.

---

### Post by Young Druid on 2009-10-03
Hm. May be you are right. 
But do you have any ideas why slowness begins only after first started application?
Could you suggest me how to check correctness of nvidia driver?

---

### Post by Young Druid on 2009-10-04
Ok. I had nvidia drivers from repository (96.43.10).
I downloaded and installed a new one from nvidia web-site 96.43.13
Nvidia setup wizard created a default xorg.conf for me.
But still the same problem. 
It's so funny. I login in system. Selection on desktop is ok. I open 'top' application (it's a panel applet for xfce). It shows that when I do selection xorg eats 16% of CPU. minimize and maximize 'top' application. Do selection on desktop. xorg eats 60% and more of CPU. When I do log out/log in I can repeat this action again.

My card is GeForce4 MX 440 SE
Some info from Xubuntu about situation.
> 
sudo glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/86257 the monitor refresh rate.
7182 frames in 5.0 seconds = 1436.212 FPS
XIO:  fatal IO error 22 (Invalid argument) on X server ":0.0"
      after 122 requests (122 known processed) with 0 events remaining.


> 
cat /var/log/Xorg.0.log | grep "(WW)"
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(WW) Warning, couldn't open module freetype
(WW) Warning, couldn't open module type1


> 
lsmod|grep agpgart
agpgart                42696  1 nvidia


> 
cat /proc/driver/nvidia/agp/status
Status: 	 Enabled
Driver: 	 NVIDIA
AGP Rate: 	 4x
Fast Writes: 	 Disabled
SBA: 		 Disabled


I'm not crazy about selection on desktop. But it seems that all UI is slow comparing to Windows XP. Selection just shows that slowness begins after first started (minimized/maximized) application.

Please, help with solving this problem.

---

