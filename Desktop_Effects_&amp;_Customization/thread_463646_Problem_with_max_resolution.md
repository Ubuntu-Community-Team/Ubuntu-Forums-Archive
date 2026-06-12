---
title: "Problem with max resolution"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by CyrusComputers on 2007-06-03
I'm trying to install Ubuntu for the first time and I'm having a small, but annoying problem. When I go into the system properties to change the resolution, I get stuck with a maximum of 800x600 on a 17" CRT monitor. If I plug in my 19" LCD monitor, then I get stuck with 1024x768. Both of these are below the NATIVE resolutions of the displays, and far below the max resolutions of the displays. The native for the 17" CRT is 1024x768 and the native for the 19" LCD is 1280x1024. Is there a config file that I can manually edit to make the other resolutions available? Is there any other way to fix this? Thanks for any help I can get, I really would like to start using Ubuntu on most or all of the PCs at the company that I own!

---

### Post by WiFi Ed on 2007-06-04
From terminal run: sudo dpkg-reconfigure -phigh xserver-xorg

It will ask you to select your video card (up/down arrows to navigate, spacebar to select, enter to save) then ask you to select your resolutions (up/down arrows to navigate, spacebar to select, enter to save).

Re-start X (Ctrl-Alt-Backspace) or just re-boot.

---

### Post by CyrusComputers on 2007-06-04
I tried what you said, but there was no change after I rebooted, it's still in 800x600 resolution. Do you have any other ideas? I'm going to be using this machine with the CRT monitor, so I'm not going to try configuring it for the larger LCD (see my first post). Does this make any difference?

---

### Post by CyrusComputers on 2007-06-05
Well, I finally figured it out by spending a TON of time on google. There were two problems which cause the resolution error. The first is that the file /etc/X11/xorg.conf didn't contain the vertical and horrizontal refresh rates of my monitor (they weren't automatically detected). THe second problem is that the same file had the default color depth at 24-bit color, where the Pentium II machine that I'm running this on (I know, it's ancient but I'm using it as NAS) can only handle 16-bit color. After those two changes it ran like a charm!

---

### Post by WiFi Ed on 2007-06-17
Glad you got it all sorted out!

My installs of Ubuntu have been relatively free of drama, and so I haven't had the "opportunity" to learn all the different ways something might not quite work right, but reading about how you and others make it work is a great education:D

---

