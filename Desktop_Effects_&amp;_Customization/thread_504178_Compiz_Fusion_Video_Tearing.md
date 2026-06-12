---
title: "Compiz Fusion Video Tearing"
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by GraveyardPC on 2007-07-18
Ok, I know there are lots of threads here for video playback tearing in Compiz Fusion. But so far, none of them have proven to be helpful to me. All I want to know, is who has an nVidia graphics card with Compiz Fusion running -- and-no-video-playback-tearing? If this applies to you, please tell me what combination of settings and drivers you are using (for ccsm and nvidia-settings*). Thank you.

Edit: I'm not using XGL right now either, but video tearing was present there as well.

---

### Post by Happy_Man on 2007-07-18
Hmmm... I don't get any tearing at all, and if I do, it's usually so minimal I don't notice it. I'm using the video playback function of Compiz Fusion, if it helps.

---

### Post by GraveyardPC on 2007-07-19
Ok, I'm going to say this one more time. I want nothing more than a person running Compiz Fusion without XGL and under an nVidia graphics card -- with an LCD using vsync -- to detail their setup to me. I want ccsm, nvidia control panel, and media player settings. I just want to get this solved, not spend my time being told, "I have it working with default settings." I'm looking for serious answers here, not redirects to forum posting here I've read over 100 times.

---

### Post by Happy_Man on 2007-07-19
Jeez... sorry. 

Uh.... If I'm not mistaken, if you've got the restricted manager drivers, that means you're not running XGL, but you've got acceleration. Splendid. All I did from there was add Trevino's repos, and install Compiz Fusion like all the howto's describe. I really am using the default settings, not some heavily tweaked customized version. I've got a nVidia Geforce 4 MX 420, with the restricted drivers, running Compiz Fusion, perfectly fine (by my standards). 

And unfortunately, I really am one of those people that have gotten it working "with the default settings". The only extra thing I have enabled in CCSM is the video playback plugin, which is why I suggested that you try it. But from what I can see, the video may not be the source of the problem. What's your graphics card? When do you get tearing? Which nVidia driver are you using? All these points can help us to diagnose your problem.

---

### Post by GraveyardPC on 2007-07-19
First off, I'm not trying to be mean, sorry if I came off like that. I'm just frustrated that no one has a straight answer. Two, the video plug-in in ccsm is on by default anyway...at it still is for me. I'm on Ubuntu 7.04 x64, running an nVidia 7800GT with default nvidia-glx-new drivers from repos. I'm getting tearing in video playback, and no where else. I have sync to vblank forced in nvidia-settings and turned off in ccsm (as it's already globally forced). I'm also in TwinView with two LCDs at 60hz refresh. Without Compiz Fusion, I have zero video tearing when using XV. I've heard switch the video output, fool with Compiz refresh rates...etc and no combination of anything I've tried has worked thus far. I'm just looking to try someone's settings that appear to work for them. I've also changed gstreamer to no XV and tried totem as well, I'm using VLC currently, and totem still tears.

---

### Post by Happy_Man on 2007-07-19
I think that maybe it isn't Fusion's fault, just more of a driver thing. Whatever it is, remember that Fusion is alpha software. More than likely your issue will be resolved through an update at some point.

---

### Post by GraveyardPC on 2007-07-19
Yea, I was afraid of that. That's why I'm keeping it off until it's fixed.

---

### Post by Happy_Man on 2007-07-19
But then.... if it's off..... how will you know when it's fixed? ;)

---

### Post by GraveyardPC on 2007-07-19
Because I turn it on and try it with different combinations of settings after every update...

---

### Post by sagara on 2007-07-25
GraveyardPC, I have your same issue.  Any progress so far on a fix?

I found this post as a posible solution, I will try it once I get home:
[http://forums.gentoo.org/viewtopic-p-4150869.html?sid=bbda4895f8de6aba3ddb8729213424b8](http://forums.gentoo.org/viewtopic-p-4150869.html?sid=bbda4895f8de6aba3ddb8729213424b8)

Let me know if it works for you.

---

### Post by GraveyardPC on 2007-07-25
Well, I just tried "nvclock" and it made absolutely no difference. The main issue is that vsync is working, but not for video playback. I'm gonna keep trying with nvclock although, I might find something new in it to solve this.

---

### Post by Kayne on 2007-07-30
I had the same problem with tearing in video files.
I tinkered a bit here and there and that's how I got it working:

In nvidia-settings all boxes regarding vsync are unchecked.
In Compiz-Fusion settings vsync is enabled and refresh rate is 200.

---

### Post by GraveyardPC on 2007-07-31
Kayne, a few questions:
1. What type of monitor are you using, LCD or CRT?
2. What media player are you using, and what video output?

---

### Post by Kayne on 2007-08-01
> **GraveyardPC said:**
> Kayne, a few questions:
1. What type of monitor are you using, LCD or CRT?
2. What media player are you using, and what video output?
I'm using a LCD (NVidia 5900XT) and totem-gstreamer. You can't change the video output here, in mplayer xv is used.
BTW, the nvidia-settings regarding vsync don't matter, I found out that for my setup the only switch that decides about tearing or non-tearing is the vsync checkbox in the compiz-fusion settings.

---

### Post by Depressed Man on 2007-08-01
You can change gstreamer's video output. I forget the command though (try searching for a subject like "changing gtstreamer's output". I think it's gstreamer-properties in the terminal though. It's been a while since I changed it. If I was in Ubuntu right now I could just copy and paste it from this file of fixes I have lol.

---

### Post by Kayne on 2007-08-01
Oh yeah, actually I forgot about it.
The output is on "automatic"...

---

### Post by jhernandez1270 on 2007-08-01
Graveyard,

Not that I know anything about anything,  but have you tried totem-xine as opposed to totem-gstreamer?  In my attempts to get video playback on my laptop with Compiz-Fusion this one worked for me.  I don't have an nVidia card, so I can't say it will work for sure but I think it's worth a shot.

totem-xine is available through the default repos so just select it in Synaptic.  It will uninstall totem-gstreamer and plugins, so after a reboot, you will need to re-install the plugins.

Hope this helps

---

### Post by sagara on 2007-08-01
I've actually noted that with the latest compiz fusion update, the tearing has decreased A LOT... it happens now rarely.

---

### Post by GraveyardPC on 2007-08-03
Well, from my experience the "Sync To VBlank" option in CCSM does absolutely nothing. If I turn off all vsync forcing in nvidia-settings and only use the one in CCSM, tearing happens all over Compiz -- and not just in video playback.

Also, I know how to change the gsteamer's video output to noXV, which I've done. I've also been through Xine, Mplayer, Totem and VLC, with all types of different vsync options (if applicable) and video ouput settings. This problem seems to stem from something related to Compiz either not detecting the correct refresh rate or the "Sync to VBlank" option not working at all. Both could possibly be happening because of TwinView or the fact that my refresh rate is reported incorrectly in Ubuntu because of the nVidia driver (which is a commonly known issue: [http://ubuntuforums.org/showthread.php?p=2269205](http://ubuntuforums.org/showthread.php?p=2269205)).

---

### Post by clearthought on 2007-12-19
using nvidia driver and compiz fusion, no xgl,  i can get rid of video tearing only for  fullscreen video by checking 'unredirect fullscreen windows' in compizconfig settings manager, General Options -> General tab.
vsync is on in nvidia-settings, and it doesn't matter what it is set to in compizconfig.
using xine with xv or xvmc output

---

### Post by hyperair on 2008-02-24
On my nVidia card I've managed to get rid of the problem, but only in Totem, by changing the video device in gstreamer-properties. Instead of "Default", I picked "NV05 Video Blitter". I reckon if there was a similar setting in other programs, you could fix this video tearing problem as well.

This article has more detail on this: [http://www.inb.uni-luebeck.de/~boehme/nvidia_xvideo_misc.html](http://www.inb.uni-luebeck.de/~boehme/nvidia_xvideo_misc.html)

---

### Post by RabidDawgr on 2008-03-07
People with 8 series cards should note these cards use xv texture adaptor . With compiz, sync to vblank for xv is then disabled. I don't know if setting vsync on in ogl settings is supposed to fix this but for me it does not

---

