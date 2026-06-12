---
title: "Playing games on a System with Dual Monitors"
date: 2009-01-20
forum: Gaming &amp; Leisure
---

### Post by AegisTalons on 2009-01-20
So I am running a dual-boot setup hooked up with dual monitors. When I go into Windows to play games, I turn off one of my monitors so that the video card can use all of its resources on one monitor.

What do you guys do for Ubuntu? I've gone into Nvidia-Settings and turned off the second monitor. Do you guys also turn off compiz, if you are running it?

---

### Post by bobisculous on 2009-01-20
While I only play one real game in Linux, I only use one of my two monitors. BZFlag is the only game I play, and when I play it I will open it in terminal using the command "bzflag -window" which of course will open it in window rather than full screen. 

I maximize it on my larger monitor, then just confine the mouse to the bzflag game screen. Works really well and I can still keep up with IMs and or chats. 

-Cameron

---

### Post by AegisTalons on 2009-01-21
Well for me, on Windows I love to play Team Fortress 2. I got it to work in Linux through Wine especially good results with [PlayOnLinux]("http://www.playonlinux.com/en"). It is running using DirectX 8 instead of 9, so it does not look so great, but it gets decent frame rate. 

Do people who play FPS or something that is hardware intense do anything special to play it, such as turning off monitors and compiz?

---

### Post by 0bso on 2009-01-21
> **AegisTalons said:**
> 
Do people who play FPS or something that is hardware intense do anything special to play it, such as turning off monitors and compiz?

I do both. But my video card is just a 6600gt so it needs all the help it can get

---

### Post by Vadi on 2009-01-22
I don't turn it off. I use the second one for chatting (don't have alt+tab).

---

### Post by 0bso on 2009-01-22
> **Vadi said:**
> I don't turn it off. I use the second one for chatting (don't have alt+tab).

I used to in windows, but in ubuntu it either severely kills my framerate or it always tries to stretch it over both monitors. I have the second monitor set up as twinview, do I need to make it it's own x-server? Or is there another setting that will keep games from always wanting to span both?

I tried to benchmark the difference but the dual monitors didn't seem to bother glxgears.

Single monitor - metacity
26301 frames in 5.0 seconds = 5260.058 FPS
28732 frames in 5.0 seconds = 5745.641 FPS
28522 frames in 5.0 seconds = 5689.106 FPS

Dual monitors - metacity
25242 frames in 5.0 seconds = 5048.374 FPS
28338 frames in 5.0 seconds = 5667.434 FPS
27986 frames in 5.0 seconds = 5597.129 FPS

Dual monitors - compiz
8886 frames in 5.0 seconds = 1777.171 FPS
10137 frames in 5.0 seconds = 2027.364 FPS
9929 frames in 5.0 seconds = 1985.703 FPS


So yeah compiz definitely gets turned off. I would leave the second monitor on if it didn't cause problems.

---

### Post by Vadi on 2009-01-22
glxgears is a horrid benchmark, don't use it. I'd recommend this: [www.phoronix-test-suite.com/](www.phoronix-test-suite.com/)

And yeah - some games to tend to strech on both screens. Haven't yet went about investigating this, I mostly play Savage 2 which can go fine on either one or two (and since two would make my char be in the middle, I play on one)

---

### Post by detrate on 2009-01-23
Back when I used xinerama on my duals, I would run a separate xorg.conf for games that would turn off one monitor for the reason mentioned above, some games would stretch across the screens.  Even if I set the resolution, it would stretch across both which is really determined by the game engine I suppose.

Since switching to twinview, things have been a lot more flexible and appear more stable.  I was able to play games full screen and watch chat in my other.  Now that I've upgraded to 2x26" monitors, I play in windowed mode on one and do whatever on the others.  Only if I REALLY serious do I turn one off.  And to do it, I just hit the power button.  I'd imagine that would save me something :).

---

### Post by AegisTalons on 2009-01-23
Can someone explain me the difference between xinerama and twinview and all the other different options available for the Nvidia-settings?

---

### Post by detrate on 2009-01-23
I'm not an expert in the field but I believe TwinView was nvidia's attempt to make up for some things xinerama couldn't offer / handle it smarter.  There are some limitations to Twinview that don't phase xinerama however.  Twinview will only work off a dual head card, you can't use 2 separate videos with it.  TwinView, as the name implies is limited to 2 monitors, xinerama can stitch together as many as you need:

[img]http://upload.wikimedia.org/wikipedia/commons/2/2b/Xinerama_4way.jpg[/img]

---

### Post by cybermatthieu on 2009-02-06
Nice pic! :D

Do you actually work with all those monitors??

---

### Post by Hitman_Forhire on 2009-12-03
> **0bso said:**
> I have the second monitor set up as twinview, do I need to make it it's own x-server? Or is there another setting that will keep games from always wanting to span both?



Can I get a bump on this thread, I have a similar setup; running seperate X screens w/ Xinerama. Nexuiz always try to span both monitors. 

I have manually added a 1280x1024 resolution but it still spans. In window mode it doesn't take up the entire monitor even with that resolution [crt].

Has anyone figured out a way to force a game/nexuiz to utilize only one monitor?

Thanks!

---

### Post by brian70809 on 2009-12-03
I use Metamodes in my xorg.conf file to make it so certain resolutions called by a game move it into one monitor.  It shuts the other monitor off..

Good luck!

here is what it says in my xorg.conf for Screen0

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: 1680x1050 +1280+0; CRT: nvidia-auto-select +0+0, DFP: 640x480 +1280+0; CRT: NULL, DFP:  1680x1050 +0+0; CRT: NULL, DFP:  1440x900 +0+0; CRT: NULL, DFP:  800x600 +0+0; CRT: NULL, DFP:  1600x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

