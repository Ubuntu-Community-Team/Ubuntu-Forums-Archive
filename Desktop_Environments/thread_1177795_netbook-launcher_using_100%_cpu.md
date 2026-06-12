---
title: "netbook-launcher using 100% cpu"
date: 2009-06-03
forum: Desktop Environments
---

### Post by chesterman on 2009-06-03
Hello people.

I'm new to the foruns, but not so new to linux. I'm a ubuntu and debian user since 2005 and work every day with linux. i'm using the jaunty netbook remix since it went out in my msi wind u100 and i'm just loving. everything worked out of the box and the system is very good.

last week i plugged a external monitor to my wind, and after some issues, it worked ok with the 2 displays, but when i got home, the netbook-launcher process is using 100% of the cpu, and is barely usable. when i'm using another app (like yakuake or firefox) and the netbook-launcher goes to background, it stop consuming cpu time, but when i go back to the main screen, it takes full load again.

right now i'm using the standard gnome desktop, but the new netbook desktop is much better for my wind.

tks in advance for any help and sorry for my poor english.

---

### Post by chesterman on 2009-06-04
anyone?

---

### Post by chesterman on 2009-06-04
i dont know if this is relevant, but i think my glxgearsis is too slow
79 frames in 5.1 seconds = 15.568 FPS
91 frames in 5.0 seconds = 18.053 FPS
111 frames in 5.0 seconds = 22.198 FPS

this is my xorg.conf is very small:


Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2515 2136
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection


i never touched the file. it was auto configured.

---

### Post by maubp on 2010-01-29
> **chesterman said:**
> i'm using the jaunty netbook remix ... the netbook-launcher process is using 100% of the cpu
Did you solve this? I think I have a similar problem.

I'm using an Acer Aspire Revo 3600, either with a monitor on VGA or a TV on HDMI, with the nVidia drivers. I've been trying the Karmic Ubuntu netbook remix 9.10 (UNR) and also a pre-release nightly of the Lucid version (what will be 10.4 later this year). I see the netbook-launcher process using 100% of the cpu (e.g. check by top in a terminal window).

---

### Post by dabagboy on 2010-02-04
> **maubp said:**
> Did you solve this? I think I have a similar problem.

I'm using an Acer Aspire Revo 3600, either with a monitor on VGA or a TV on HDMI, with the nVidia drivers. I've been trying the Karmic Ubuntu netbook remix 9.10 (UNR) and also a pre-release nightly of the Lucid version (what will be 10.4 later this year). I see the netbook-launcher process using 100% of the cpu (e.g. check by top in a terminal window).


Bump, Same Revo 3600 same problem exactly.

---

### Post by drewcox on 2010-03-01
I am seeing the same issue with a fresh install of 9.10 Netbook Remix on a HP/Compaq TC1100 convertable tablet.  It has a Nvidia Geforce 420 Go 32M chipset.  I believe I have seen another user with this issue on this model.

Problem appears both before and after installing the Nvidia drivers successfully.  OpenGL seems to be working, the glx demos (glxgears etc) seem to work fine with 800-1000 fps.  Applications seem to work fine, but any interaction with the netbook-launcher is extrememly slow and the process takes 80-100% CPU for several seconds after.  Pretty much what others are saying...

Would love to get this working better, as it seems like a great replacement for the native WinXP on this machine for basic surfing etc.

---

### Post by sloty on 2010-03-08
> **drewcox said:**
> I am seeing the same issue with a fresh install of 9.10 Netbook Remix on a HP/Compaq TC1100 convertable tablet.  It has a Nvidia Geforce 420 Go 32M chipset.  I believe I have seen another user with this issue on this model.

Problem appears both before and after installing the Nvidia drivers successfully.  OpenGL seems to be working, the glx demos (glxgears etc) seem to work fine with 800-1000 fps.  Applications seem to work fine, but any interaction with the netbook-launcher is extrememly slow and the process takes 80-100% CPU for several seconds after.  Pretty much what others are saying...

Would love to get this working better, as it seems like a great replacement for the native WinXP on this machine for basic surfing etc.

I&#7743; having the same problems on my TC1100.  Curruntly i'm running Ubuntu 9.10 . When i in install the NBR launcher it's verry verry slow. Does anyone  know how to fix this?

---

### Post by Skaperen on 2010-03-08
Saw the same on an ASUS EeePC 900.  I was just trying out NBR and for many reasons decided to go back to regular Ubuntu.  But it was doing the 100% CPU thing and really slow when I did have NBR on it.

---

### Post by groggluebutt on 2010-04-12
I have what seems to be the same issue on an Dell Latitude C840 running the proprietary NVidia drivers.

lspci says I have a GeForce4 440:
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] 9rev a3)

glxgears gives:
5474 frames in 5.0 seconds
5652 frames in 5.0 seconds
9518 frames in 5.0 seconds
10944 frames in 5.0 seconds

netbook-launcher is very slow to respond to mouse clicks, slow to draw updates.  CPU goes to 100% when netbook-launcher is in the foreground and I try to click on anything.

This is a laptop that was running 8.10, and I upgraded to 9.10.

---

### Post by JanMalte on 2010-04-30
It seems like this is a know problem:
[https://bugs.edge.launchpad.net/linux/+bug/349314](https://bugs.edge.launchpad.net/linux/+bug/349314)
[http://ubuntuforums.org/showthread.php?t=870317](http://ubuntuforums.org/showthread.php?t=870317)

Poorly i have no solution for it at all and stick with the same problem. So if anyone could help it would be great. I want to use the nice Lucid on my Dell Inspirion 1525

---

### Post by diego_dambra on 2010-09-29
I had same problem, the issue was in /etc/X11/xorg.conf, removed:

Section "Module"
	Load	"glx"
EndSection

I believe the section was added by proprietary NVidia driver.  

CPU load is now back to normal - Ubuntu Netbook Edition 10.04

---

### Post by Fabben23 on 2010-11-11
I installed Ubuntu Netbook Remix on an old PC with a 24" monitor attached. I had all the problems listed here. Mainly mouse usuable, main screen unresponsive and netbook-launcher running at 100%

After a month of trying various things and getting nowhere - I was ready to give up.
Then I tried changing the screen resolution - IT WORKED. :)

Then I tried all the resolutions for my monitor - some work and some don't. It's a night and day difference. If it works, it works very well but if it doesn't work, it's unusable.

Can it be that something that had me perplexed for so long, just needs the monitor's resolution tweaked a little and then it's fixed?

---

