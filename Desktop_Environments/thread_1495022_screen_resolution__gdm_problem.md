---
title: "screen resolution / gdm problem"
date: 2010-05-27
forum: Desktop Environments
---

### Post by st0kes on 2010-05-27
I am very happy with Ubuntu Lucid, on the whole, but I have 2 niggly things that I don't know how to fix. 

My laptop in an HP Elitebook 6930p. The native screen resolution is 1280x800 with a refresh rate of 60hz. About 50% of the time when I boot up, the resolution is correct. The other 50% I have to change the resolution from 1024x768 as it is incorrectly detected. Once in a while I plug the laptop into my Samsung TV, maybe that has messed it up somehow, I don't know but it's a bit annoying. 

The other issue is GDM. Often I don't get the logon box, I just get the wallpaper and bottom bar. I have to switch to another virtual terminal and then back to ctrl+alt+f7 to make it appear. Does that happen to anyone else or just me?

Are there any obvious solutions to my odd problems?

---

### Post by WinRiddance on 2010-05-27
> **st0kes said:**
> My laptop in an HP Elitebook 6930p. The native screen resolution is 1280x800 with a refresh rate of 60hz. About 50% of the time when I boot up, the resolution is correct. The other 50% I have to change the resolution from 1024x768 as it is incorrectly detected. Once in a while I plug the laptop into my Samsung TV, maybe that has messed it up somehow, I don't know but it's a bit annoying. 

Are there any obvious solutions to my odd problems?
.
I can't help you with the GDM issue but the resolution problem is more than likely related to your TV. Ubuntu always recognizes the laptop display first until it's told to do otherwise. In the previous version of Ubuntu this was the case even after a restart ... causing the user to often have to reconfigure the displays once again. Well, in Lucid this issue has finally been fixed (at least to me it was an annoying issue). Now Lucid "remembers" what the last display settings were and restores them automatically during a reboot if at that time both devices are connected. If nothing external is connected to the laptop then the default laptop display should automatically be configured.

Are you sure that your laptop had the 1280 X 800 and not the other way around? I'm asking because Ubuntu frequently doesn't have the displays set in the proper left/right order under the display settings. Perhaps your TV had the 1280 X 800 setting which would explain why Ubuntu defaults to the 1024 X 768 setting when the TV is no longer connected to your laptop ... ???
.

---

### Post by st0kes on 2010-05-27
Well the TV is 32" and has a much larger resolution than the laptop. I too suspect it may be the problem though ... is there a way to make Ubuntu forget it was ever plugged into an external display?

---

### Post by WinRiddance on 2010-05-27
> **st0kes said:**
> Well the TV is 32" and has a much larger resolution than the laptop. I too suspect it may be the problem though ... is there a way to make Ubuntu forget it was ever plugged into an external display?
.
Well, I'm going to have to assume that you configured both displays, TV and laptop, in your display settings, right? If both of the displays show up in your display settings then you should be able to completely disable one of them. Just be sure to click on APPLY SETTINGS afterwards in order to save what you just changed. Reboot your machine and see what happens? If you didn't use the default Ubuntu display manager/settings then Ubuntu might be getting "confused" between the default display settings and a display control center from the graphic chip manufacturer ??? Ubuntu display settings and some AMD Catalyst control Center settings definitely do not like each other at all ....

---

### Post by fred0scan on 2010-05-27
I just install today Ubuntu dual boot with windows 7. I was having the  same exact problem. I went directly to NVIDIA website and download the drivers for Linux and when I restart the computer still mess up but did allow me to make changes on the screen resolution and its working perfect..... :guitar:

---

