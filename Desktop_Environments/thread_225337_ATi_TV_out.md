---
title: "ATi TV out"
date: 2006-07-29
forum: Desktop Environments
---

### Post by GregaS on 2006-07-29
I have Radeon 9600xt with tv out and I installed drivers for ati.com not from repositories. I connect TV with s-video cable and when I play video I only see it on monitor but on TV (I see desktop). I know that primary and secondary screens has to be changed (monitor has to be secondary screen and TV has to be primary screen). If I change that with fglrx control it says I have to restart KDE so I do ctrl+alt+backspace to restart KDE. When KDE loads again monitor is primary screen again. Does anyone have any ideas?

---

### Post by GregaS on 2006-07-30
Anyone?

---

### Post by Dr_Willis on 2006-07-30
Just to clarify, you mean to say that when you play a video in say 'vlc' the video player and video appears on the computer monitor, but on the tv output, the player is showing a black window, where the video should be.

I was having the same problem.  

But then it started working after i twiddled with a few things. Not sure what fixed it.  (it may of just needed a reboot)  My xorg.conf has a section like the following..


Section "Device"
  Identifier "ATI Technologies, Inc. Radeon R300 ND [Radeon 9700 Pro]"
  Driver "fglrx"
  option "VideoOverlay" "on"
  BusID "PCI:1:0:0"
EndSection

i THink the videooverlay is the imporntant change i did.

I followed the ati wiki page. So your issue may differ.

---

### Post by GregaS on 2006-07-30
This is my xorg.conf:

> Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

---

### Post by Nicksha on 2006-07-30
Video is being show on overlay, which can be on only one display at the time. You don't have to change primary and secondary monitors, use this command instead:

aticonfig --overlay-on=1

1 is for tv, 0 is for monitor.

---

### Post by GregaS on 2006-07-30
And if I want to watch video on computer monitor? I just use this: aticonfig --overlay-on=0 ?

---

### Post by Nicksha on 2006-07-31
Yeah, that's it.

---

### Post by Nicksha on 2006-07-31
Wait a minute! I thought you said you installed drivers from ATI's site, but your xorg.conf shows that you're still using opensource drivers. You should change the line

Driver "ati"

to

Driver "fglrx"

---

