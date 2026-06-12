---
title: "Vsync, Tearing, Compiz...solution?"
date: 2010-12-15
forum: Desktop Environments
---

### Post by Oranges10e on 2010-12-15
Hi,

I think I found a combination, that could fix this problem. I have been trying around the past few weeks and asking in different forums. Eveyone suggests something else, so I will post what I did, to get rid of the Vsync/tearing issue, in combination with Compiz (I play 720 and 1080p Videos without a prob. now and with no tearing whatsoever). Tested with Ubuntu 10.10.

1) Download **CCSM** and install it. Make sure you have the new Nvidia drivers (prop.), that Ubuntu should offer you.

2) **Enable Vsync in CCSM** (general options/settings) and **disable** the automatic refreshrate detection (it always gets it wrong with Nvidia cards) and set it **manually** to **60 **or** 120**.

3) Do a **sudo nvidia-settings** in the terminal and **enable** Vsync for **XV** and **OpenGL** (Video and 3D) and allow **flipping **in** OpenGL**.

So far so good, eh? Nothing special so far. I always had tearing, even with all these settings, **BUT** recently I added this:

4) Open up your **xorg.conf** by doing a **sudo gedit /etc/X11/xorg.conf** in the terminal and putting this in the file that opens (where the other Device/Screen Options are listed): **Option "TripleBuffer" "True"**

5) Save and reboot your computer, just to be sure.

6) Done. If you want accelerated Video and you have an Nvidia card, you could also use VDPAU. Download Mplayer via Software Center and enable VDPAU as output there. Works only with Gefore 8 series and above. Also, I have been testing the new Adobe Flash 10.2 Beta and everything seems to be working O.K. No tearing with flash, no tearing with videos, no tearing on the desktop. Everything awesome so far.



If anyone wants to try it out and report back, do so! I would like to know if I am just having good luck or if this actually helps reduce tearing. I have yet to see any tearing at ALL.

I have done this in many 3D games, so I thought it might help with Compiz, since I never read about anyone trying this combination. 

Vsync ON: Performance decrease but no tearing.
Vsync ON and DoubleBuffer: Performance is better but framerate ist "cut" in half. Example: 60hz LCD; if you can't get those steady 60fps and sink a few fps below those 60fps then you're at 30fps suddenly. During this I sometimes see tearing.
Vsync ON and TripleBuffer: Performance is at its best but it also eats up 50-60% more VRAM. If you have enough VRAM, then this should be no problem. No tearing whatsoever.


I will try these steps with an ATI card. I have tested Compiz with Intel GMA chipsets (GMA 900 and 950) and it seems to do Vsync just fine, even without adjusting things and all.

Oranges :popcorn:

---

### Post by a-user on 2010-12-15
this troubled me for a long long time, too. and i also did what you wrote. and indeed it makes things better, but for me still not usuable.

watch a video in fullscreen with your settings but select a scene where the camera moves with constant speed around, not too fast but neither slow.

do you observe some kind of "jump" around every one second oder every two? a slight stutter?

no? try deactive the composite extension within the xorg.conf. watch this movie again. i bet it will look more fluent.


now to explain what i'm talking about: the vsync problems are still not solved with compiz and nvidia, and according to compiz developer forums it won't get fixed on their side (they claim its a bug in nvidia drivers and the refuse to make a workaround... details are not important here).

now, you can get vsync, but not 100% reliable. this results in this periodical small jumps/stutters. if you don't care about this, lucky you. but it drives me crazy.

hence i had to disable compiz-extension.

---

### Post by Oranges10e on 2010-12-16
Hi,

thanks for your feedback.

I have no jumping in frames, no stutter or anything like that at all (I know what you are talking about, though). 

I am connected to a 42" Plasma and everything runs and is very fluid; without tearing or stutter (remember, you need a minimum of 128MB VRAM to run Compiz with Vsync and TripleBuffer). I can make a screenshot or maybe record the desktop with a vid running, if you want? I can play a video and let some other programs run and then I could turn the cube around a bit. Usually things would tear up or stutter, due to the heavy load and because it was never really synced that well - not in my case as it is now. 

Have you activated the redirect fullscreen windows option within Compiz?

I know about the "not 100% Vsync" and "it's Nvidias fault" issue. I have spoken with AaronP about this, some time ago, and he told me it was a problem with Compiz (I even posted a thread back then and a poll, asking who actually cares about Vsync). 

Anyway, I will be playing around with it some more. Up untill now, and I have been using it this way the last few days - no issues so far.

Oranges

---

### Post by Krytarik on 2010-12-16
> **Oranges10e said:**
> Have you activated the redirect fullscreen windows option within Compiz?
Is it activated at our machine? (actually "unredirect")

I've tried this option after upgrading to 10.04 (from 7.10), and the performance of fullscreen-video is indeed better, but there is an apparently common glitch at my machine because of the different handling of the "window". Each time you exit fullscreen the desktop-background is shown for a second or so, the background also "flickers through" the fullscreen display if I move the mouse out of the video-area, e.g. to the controls.
Thus I deactivated this option again and tweaked the player-options to get the best results as possible. But I still sometimes observe the behavior a-user describes, at least a little bit. Disabling composite delivers the best results, but of course it also disables the desktop effects.

Greetings

---

### Post by a-user on 2010-12-20
@[Oranges10e]("http://ubuntuforums.org/member.php?u=938859"): oh wait, you have an ati-card, right? as far as i know, the effect i described is a nvidia problem related to compiz.
sorry

---

### Post by wapko on 2011-01-08
believe it or not, but this actually helped reduce the tearing in my vdpau accelerated h.264 720p video files. there is still tearing. but not as much. even in panning shots :)
thank you! 

running 10.04/compiz on an asus ul30vt. geforce 210m

---

### Post by onemanclapping on 2011-01-17
Hey! I did all this, nothing happened...

Btw, my xorg.conf looks like this:
```
 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option "TripleBuffer" "True"
EndSection

Section "DRI"
	Mode 0666
	EndSection
	Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

Is there something wrong? If I disable compiz, vsync works fine, but like this even moving a window from let to right slowly you can see a lot of tearing - specially in a line at the top.

VDPAU also tears (a lot) with compiz...

Any thoughts?

---

### Post by Hydrohs on 2011-01-23
Just wanted to thank you for this. It's been bugging me for a while, but your solution worked for me. I've got an Nvidia GT330M. Fixed tearing in Mplayer as well as Flash.

---

### Post by kev77 on 2011-02-17
Thanks! worked perfect on macbook pro dual core - ssanta rosa.  ;)

---

### Post by mcpish on 2011-08-24
Thank you so much.  I've been having this problem for what seems like FOREVER!

This completely fixed it.  Perfect tear-free desktop, silky smooth video in mplayer, no tears.

Awesome!

---

