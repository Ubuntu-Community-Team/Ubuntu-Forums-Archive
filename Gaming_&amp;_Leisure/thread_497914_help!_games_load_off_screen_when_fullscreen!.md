---
title: "help! games load off screen when fullscreen!"
date: 2007-07-10
forum: Gaming &amp; Leisure
---

### Post by bbooker5 on 2007-07-10
Hi. I have a dual-monitor setup with an nvidia card. I have all of my drivers up to date. I am running Ubuntu Studio. Also, Beryl is running.

Whenever I run any game that needs to go fullscreen, the game is being displayed very strangely. I can only see half of the content. This has happened to me with UT2003 as well as every full screen game I've tried installing from Synaptic. I have a 22" and a 19" monitor and I can see half of it on the 19". I would like to make it display on the first monitor (22"). It's not like it's half on one screen and half on the other - it's far off the right side of the right monitor.

I am not sure if there is anything I need to post to help but I would be more than willing to do so!

Thanks so much.

Ubuntu rocks. I've been running it for a week and haven't even thought about loading XP again.

Cheers.
[http://myspace.com/horriblecircuit](http://myspace.com/horriblecircuit)

---

### Post by MCMcButtah on 2007-07-11
I have this exact same problem so I am assuming you have an nvidia card. This seems to happen only if your primary monitor is on the right. How annoying is that? What I do when I want to play a game is to turn off the secondary monitor so I only have one display. This also effects amarok visualizations when they are full screen. I don't know why this doesn't seem to effect more people. I am guessing maybe most people have thier primary monitors on the left?

Here is a thread on the nvidia forum discussing this. I'v tried a few times to start threads on this, but nvidia never answers or even indicates that they are at least aware of the problem.

[http://www.nvnews.net/vbulletin/showthread.php?t=94076](http://www.nvnews.net/vbulletin/showthread.php?t=94076)

---

### Post by Spam Banjo on 2007-07-23
I got a similar problem, which is probably nothing like. I simply want to be able to full screen apps on one of the screens, but at the moment they full-screen over both.

I am using Beryl under ATI (X1300) open source drivers, and only get this problem when I use my Xgl login.

Xgl mode also causes the 'Ctrl' key on my keyboard to stop functioning. Which is extremely irritating. I am a web designer, so I use shortcuts lots.

Please help me someone!!!
I love the Ub.

---

### Post by vinx on 2009-04-10
I can confirm this is still a problem. I have this problem with Wine-games, when my second monitor is enabled with xinerama/twinview. If I use "separate X screen" the games work just fine.

My setup: laptop (HP compaq 8710p) with onboard nVidia-video (DirectX 10 capable), Ubuntu 9.04beta (same problem on 8.10), second monitor **left of** the laptop. I personally think it is a Xinerama-bug; what do you think?

Part of xorg.conf:

Section "Screen"
	Identifier     "Screen0"
	Device         "VideoDevice0"
	Monitor        "Monitor0"
	Option         "Coolbits" "1"
	Option         "SecondMonitorHorizSync" "24.0 - 83.0"
	Option         "SecondMonitorVertRefresh" "55.0 - 75.0"
	Option         "TwinView" "1"
	Option         "TwinViewXineramaInfoOrder" "DFP-0"
	Option         "metamodes" "DFP: 1680x1050_60 +1680+0, CRT: 1680x1050_60 +0+0"
	DefaultDepth	24
	SubSection "Display"
		Depth       16
	EndSubSection
EndSection

I've seen a solution with
#	Option	"MetaModes" "1680x1050, 1680x1050; 1680x1050+0+0, NULL; 1440x900+0+0, NULL; 1280x1024+0+0, NULL; 1280x768+0+0, NULL; 1024x768+0+0, NULL; 800x600+0+0, NULL; 640x480+0+0, NULL;"
to just turn off a monitor when playing games, but that did not work for me.

---

