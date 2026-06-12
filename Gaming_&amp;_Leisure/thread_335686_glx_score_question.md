---
title: "glx score question"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by jinxy1919 on 2007-01-10
IS it the lower the number the better or what this is my score

855 frames in 5.0 seconds = 170.786 FPS
890 frames in 5.0 seconds = 177.992 FPS
875 frames in 5.0 seconds = 174.968 FPS
863 frames in 5.0 seconds = 172.329 FPS
892 frames in 5.0 seconds = 178.390 FPS
889 frames in 5.0 seconds = 177.790 FPS
864 frames in 5.0 seconds = 172.788 FPS


Is that good or bad am i going to be able to run css with good frames? i do on windows get really good frames

---

### Post by Jussi Kukkonen on 2007-01-10
FPS is frames per second. Higher figure is better. 170 is a pretty low figure -- you probably do not have 3D acceleration in use (depending on your card it could be even thousands of frames per second).

---

### Post by jinxy1919 on 2007-01-10
hmmm i have the new ati drivers installed i have the x850 pro and i still get 40-60 fps in cs source how do i enable all this stuff to get the best out of my card?

---

### Post by Jussi Kukkonen on 2007-01-10
40fps in a complex 3D game implies that things are going ok, so I could be wrong, but I do believe a modern card should be closer to thousands FPS in that test... I have to admit that I'm the last person to talk about this, since I don't really do 3D.

This is the command you are running, right? ***glxgears -iacknowledgethatthistoolisnotabenchmark***

---

### Post by jester45 on 2007-01-10
i ran this on a 400mhz with a ati radeon 9250 and i got 750ish so you might have a problem

are you sure you have /etc/X11/xorg.conf using the "fglrx" driver and not "ati"

---

### Post by The Noble on 2007-01-10
You should be getting at least 3000 fps, and that is accounting for the horrible ATI drivers in linux. I get 2000 fps on an Nvidia 5200 Go, so use that as a comparison. Check the thread of all the results people are getting and compare yours to another x850 owner.

---

### Post by Bozebus on 2007-01-10
3000 fps is incredibly fast. I get 420-620 on ati radeon 9550, with latest ati drivers. Running Xubuntu 6.06 on a Athlon XP running at 1250 Mhz... I know, gimp gear.... And this is my xorg.conf setting:

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9550]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Doom3 runs great, Planescape runs great, Diablo2 in Ceega runs fine. If I could JUSY get my EverQuest to stop being Soooo slow and choppy,,,

---

### Post by jinxy1919 on 2007-01-10
should i use cedgea instead of wine? will my games run way better?

---

