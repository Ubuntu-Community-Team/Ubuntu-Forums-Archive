---
title: "Wrong screen resolution"
date: 2009-06-08
forum: General Help
---

### Post by browndog289 on 2009-06-08
Hello

I have been setting up an old system with Ubuntu 9.04 with XFCE as the desktop and kaffeine as a DVB & media player.

I had everything working fine on my monitor at 1024x768 and I installed the system in the room that it is going in (with an old generic brand 4:3 tft). However when I booted the system it is coming up with something like 960x600 as the resolution and as this monitor is not widescreen the image is lost to the left and right. I went into the Display settings and selected 800x600 from the list and pressed Apply - everything fitted in and I thought great! However as soon as I rebooted the 960x600 resolution returned!

Clearly I can't be manually changing the resolution every time! 
I looked at my xorg.conf file and everything was down as Generic values - "Generic Screen" etc.
I also tried running dpkg-reconfigure xorg after stopping gdm but that only took me through keyboard options and nothing was mentioned about the screen.

I tried manually adding an "800x600" modeline but I then got an error starting x so I reverted to the old xorg.conf and it started again.

The system I am using is an old ECS M841LR board with integrated SiS graphics. It obviously works at 800x600 so how do I set it to always use this mode?

Help!

Thanks in advance!

browndog

---

### Post by browndog289 on 2009-06-09
I managed to solve this one myself in case anyone else is having display problems.

It seems to be caused by either ubuntu not correctly identifying the monitors refresh rates or by the monitor not reporting them properly.

I changed my xorg.conf file by modifying a couple of sections as follows:

Section "Monitor"
	Identifier	"Configured Monitor"
      Option      "DPMS"  "true"
      HorizSync    30.0-60.0
      VertRefresh  50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
      DefaultDepth      24
      SubSection "Display"
                  Depth         24
                  Modes         "1024x768" "800x600"
      EndSubSection
      
EndSection

It's working great now at 1024x768.

---

