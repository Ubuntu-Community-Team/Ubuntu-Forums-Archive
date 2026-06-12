---
title: "Choppy Video Problem"
date: 2005-09-28
forum: Desktop Environments
---

### Post by BIGtrouble77 on 2005-09-28
I know this one has been beaten to death here, but I'm still looking for a fix...

Ttying to play media without choppy playback.  Small stuff seems to work fine.  Larger stuff like DVD's and HD videos have major issues.  DVD playback is extremely choppy while HD playback is like watching a slide show.

Few things: 
DMA is enabled and working.
openGL is working for my ATI 9700mobile

I think the problem has to do with my video renderer.  Perhaps it's my driver, but I'd like to rule everything else out before I try replacing it because I know i'll hose my system.

I've tried playback in Xine, VLC, kaffeine and totem.   VLC plays back pretty well when I set playback to opengl video output.  HD video is still choppy, but it's noticably better and kinda viewable- audio sync is fine.  Xine does not appear to support opengl playback, so no matter what I do it plays terrible.  

Any suggestions?  

TIA!!!
-BT

System Specs:
Hypersonic AX7 Laptop
Athlon 3700+ DTR
Radeon 9700 mobile
2gb DDR SDRam
7200RPM 60gb HD

---

### Post by gorkhal on 2005-09-28
did you try xine, using 'xv' as the video driver from the settings dialog. also check that the video sink in multimedia systems selector is set to 'Xwindows (x11/xshm/xv).

i've a pretty slow computer...but avi's and dvd's play fine, but i am below the requirements for hdtv so cant really say anything about that.

---

### Post by mlomker on 2005-09-28
> openGL is working for my ATI 9700mobile


I have almost the same hardware and I don't have any problems with DVD playback in Kaffeine.  What version of the fglrx driver are you using and what is your fps in glxgears?

```

fglrxinfo
glxgears

```

---

### Post by BIGtrouble77 on 2005-09-28
Thanks for responding guys, I really appreciate it.

gorkhal,
I changed the renderer to 'xv', but it's still extremely choppy.  I looked everywhere and could not find the 'multimedia systems selector' so I couldn't verify that setting.

mlomker,
Here's the fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

I know it's kinda old...

Here's the GlxGears:
6645 frames in 5.0 seconds = 1329.000 FPS
8333 frames in 5.0 seconds = 1666.600 FPS
8380 frames in 5.0 seconds = 1676.000 FPS

(I should probably follow your giude and update the video drivers)

Thanks again,
-BT

---

### Post by mlomker on 2005-09-28
> 6645 frames in 5.0 seconds = 1329.000 FPS

Not so great.  I get 2200-2500 with the same card.  If you have a [Uniwill]("http://www.uniwill.com/products/performance/258ka0/258ka0.php?HL=2&P=2") like me, then you'll want to use the 8.14.13 driver because the latest one misdetects the Samsung LCD panel's resolution.

---

### Post by BIGtrouble77 on 2005-09-28
[QUOTE=mlomker]Not so great.  I get 2200-2500 with the same card.  If you have a Uniwill like me, then you'll want to use the 8.14.13 driver because the latest one misdetects the Samsung LCD panel's resolution.[/QUOTE]
That's what I was afraid of.  I'll try and tackle it tonight.  BTW, do you have the Clevoe D47K chassis?  If so, were you able to get the multi card reader working?  I still haven't found a driver for it yet.

Thanks,
-BT

Edit: I just noticed the link, it's a completely different chassis.

---

### Post by mlomker on 2005-09-28
If you're referring to the **O2 Micro** controller then I've already looked into it and there isn't a linux driver at all.  The company won't release the specs.

---

### Post by BIGtrouble77 on 2005-09-28
[QUOTE=mlomker]If you're referring to the **O2 Micro** controller then I've already looked into it and there isn't a linux driver at all.  The company won't release the specs.[/QUOTE]
I think it might be different.  I just get 3 unknown winbond devices in the device manager.  So there may be some hope after all.  I have to do some more research after I get this video thing working.

---

### Post by BIGtrouble77 on 2005-09-29
Well, I just updated my drivers from the most recent ATI installer.  Framerates are now double what they were.  Only thing I had to do was manually add my resolution in the xorg.conf.  

Unfortunately, my video is still extremely choppy.  DVD's look great if I play them in a window at 720x480, but once I try and scale it larger or play full screen playback is terrible.  

Hopefully someone has a few more suggestions... :confused: 

-BT

---

### Post by mlomker on 2005-09-29
> at 720x480, but once I try and scale it larger or play full screen playback is terrible.  

Ah, I don't think your post mentioned that you were scaling it.  I always watch mine full-screen but with the largish black borders.  I'm one of those video-snobs that will only watch things in their original aspect ratio.  :D

---

### Post by raven on 2005-09-29
BIGtrouble77 I do not want to change the way you are going to tackle this problem
cause I do not know the solution
but I have PIII450 512 ram, nvidia drivers
and my fps sucks look at the results
2861 frames in 5.0 seconds = 572.200 FPS
2636 frames in 5.0 seconds = 527.200 FPS
2639 frames in 5.0 seconds = 527.800 FPS

but I don't have any choppy video play back (DVD, HD,stream)
in kaffeine, vlc, realplayer, totemxine
just to let you know
good luck

mlomker, I do not want to hijack the thread but when I use  the command fglrxinfo
I get "bash: fglrxinfo: command not found", do I have to install any package,
and how do I know my open GL is working fine? and a possibility to get better fps ???

---

### Post by markr on 2005-09-29
Kinda obvious, but have you enabled DMA for your DVD player using something like :

hdparm -d1c1 /dev/dvd

If this works you can make it permanent by putting it in '/etc/init.d/bootmisc.sh' at the end but befire the Exit line.

Mark.

---

### Post by cbudden on 2005-09-29
How do you get glxgears to show the FPS.  When I run it from the terminal, all i get are gears.

---

### Post by mlomker on 2005-09-29
> mlomker, I do not want to hijack the thread but when I use  the command fglrxinfo
I get "bash: fglrxinfo: command not found", do I have to install any package,


The OP has an ATI card.

---

### Post by mlomker on 2005-09-29
[QUOTE=cbudden]How do you get glxgears to show the FPS.  When I run it from the terminal, all i get are gears.[/QUOTE]

[You are running Breezy.]("http://www.ubuntuforums.org/showthread.php?t=64273")

My posts are tailored to the OP, not a general audience...

---

### Post by BIGtrouble77 on 2005-09-29
[QUOTE=mlomker]Ah, I don't think your post mentioned that you were scaling it.  I always watch mine full-screen but with the largish black borders.  I'm one of those video-snobs that will only watch things in their original aspect ratio.  :D[/QUOTE]

It's scaled to the correct aspect ratio.  I just meant watching it in a window at 720x480 works perfectly.  Trying to do full screen (at the same aspect ratio) is problematic.  

I'm forced to resize my hd movies because they are larger than my display res.

Interesting thing is my desktop machine (with ubuntu) works perfectly.  Once I enabled dma on that machine life was great.  I have a geforce6800gt on that machine.

---

### Post by mlomker on 2005-09-29
> It's scaled to the correct aspect ratio.  

You are correct.  I should have said that I don't use scaling. 

What program are you using?  I didn't notice a scaling option in Kaffeine.

---

### Post by BIGtrouble77 on 2005-09-29
[QUOTE=mlomker]You are correct.  I should have said that I don't use scaling. 

What program are you using?  I didn't notice a scaling option in Kaffeine.[/QUOTE]

I think I know where the confusion is... Do you have scaling turned off in your bios?  With some laptops you can turn scaling off in the bios and it will prevent programs from not running out of the lcd's native resolution (you'll just see black border bars).  Scaling DVD's is a pretty standard function, tho.  

With current ATI and NVidia cards you can set that in the drivers (in windows).    But DVD's, in windows, will still play fullscreen even if the system is set not to scale displays out of the native resolution.  Maybe that's different in linux.  If you choose  fullscreen the dvd should span the entire screen either vertically or horizontaly (depends on the aspect ratio of the movie and your screen dimensions).  

Programs like xine will scale the image up to fit your screen and improve the picture.  Unfortunately, on my machine I take a HUGE performance hit.  I still think it's a video rendering issue.

---

### Post by cbudden on 2005-09-29
[QUOTE=mlomker][You are running Breezy.]("http://www.ubuntuforums.org/showthread.php?t=64273")
My posts are tailored to the OP, not a general audience...[/QUOTE]

Sorry, i didn't bother searching.  but this works 
```
 glxgears -iacknowledgethatthistoolisnotabenchmark 
```

---

### Post by BIGtrouble77 on 2005-10-02
Well, I finally fixed the problem!!!

I noticed that running 'xvinfo' showed that no overlays were active.  

I checked out my xorg.conf and noticed that:
Option "VideoOverlay"               "on"
Which is correct...

After turning off:
Option "OpenGLOverlay"              "off"
Option "UseInternalAGPGART"         "no"

and restarting X, xvinfo finally show'd that there was an active overlay.  Now DVD's appear to run perfectly full screen while using the xv overlay option.

Thanks to everyone for their suggestions.

-BT

---

### Post by Dolphin on 2005-10-02
edit: missed

---

