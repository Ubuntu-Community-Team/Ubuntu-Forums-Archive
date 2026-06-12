---
title: "Americas Army - Starts to Load then Dissapears"
date: 2006-06-04
forum: Gaming &amp; Leisure
---

### Post by Ted_Smith on 2006-06-04
Apologies if posted elsewhere - search yileded no results for me. 

I have re-installed Americas Army (AA) on Ubuntu Breezy (after a failed upgrade to Dapper I had to revert back to Breezy). But whenever I execute the program I get the small Americas Army logo appear in the middle of the screen for a few seconds, but then it dissapears and the game never actually loads. Any ideas anyone? (I did have it working previously before I re-installed Breezy).

Thanks

Ted

---

### Post by erimar77 on 2006-06-04
do you have 3d acceleration going?

---

### Post by Ted_Smith on 2006-06-04
How do I determine that and if I have what is the solution\cause? Thanks

Ted

---

### Post by erimar77 on 2006-06-04
i know it's not a benchmark utility or anything, but try $glxgears -printfps  to see what the frame rates are like.

---

### Post by Ted_Smith on 2006-06-05
It reports the folloing : 
```

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

I have already installed the latest Nvidia drivers using the HOWTO guide written by TSElliot here in the forums. The installer I used was 'NVIDIA-Linux-x86-1.0-8762-pkg1.run' Because it's 8762 I skipped a couple of steps in his guide because he says 'If you're using the driver 8174 or higher you MUST skip to step 13". Well that's what I did. However, since reading your response I did the following : 

Looked up the results on google and ensured that 'Load GLX' appears in the modules area of my etc/X11/xorg.conf file, which it does anyway :

```

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"

```

Additionally (and perhaps crucially) I can't tell Ubuntu to use the Nvidia driver specifically and instead I am having ot use the generic nv one. I would have thought the Nvidia installer would have done this, but clearly not. : 

```

Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"nv"
	BusID		"PCI:2:0:0"

```

If I change it to 'nvidia' I can't use the GUI at all. It harps on at me about the fact that my kernal is built for 7677 but the module in use is 8762 or something? 

Does that make sense to you or anyone?

Thanks

Ted

---

### Post by Ted_Smith on 2006-06-05
By cheating...I mean by using Automatix, I seem to have managed to get a working installtation of the NVIDIA drivers. When I say that, everything is as it was before, except the Automatix install has managed to change 'nv' to 'nvidia' and I can still use X with all my resolution options.

However, AA still doesn't load, and glxgears reports the same error as reported above still. So I'm still no closer it seems. And yes, GLX is loaded in etc/X11/xorg.conf. 

glxinfo reports the following : 

```

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
ted@mainunit:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None    ...............to infinit....

```

Linux Kernal : 2.6.12-10-386 BTW

So then I went and looked at var/log/Xorg.0.log and I noticed :

```

(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000041gl
(EE) Failed to load /usr/X11R6/lib/modules/extensions/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

```

Further down the file towards the end it says : '(II) Loading extension NV-GLX' followed soon after with '(EE) NVIDIA(0): Failed to load GLX'. Rather annoyingly, after much searching (via google) I found this Ubuntu posting that documents the exact same problem, but no fix!!! [http://www.ubuntuforums.org/showthread.php?t=123770](http://www.ubuntuforums.org/showthread.php?t=123770)

So, quite clearly, there's a problem with GLX and Ubuntu isn't loading it for some reason. But why? Any more clues?  Are there some other commands I can type and see what their output is? There's only so much a Newbie can do on his own :-)

Ted

---

### Post by tseliot on 2006-06-06
Can you try my script?
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by Ted_Smith on 2006-06-06
Thanks TSelliot for suggesting that - you have spent a lot of your time helping people with their NVidia kit. 

I have just tried the one for Breezy and the 8756 driver but I got errors : Unable to load kernal module 'nvidia.ko'. it went on saying about incorrect kernals etc. So I used the 'uninstall' feature which went OK, but then when I ran it again and chose 'install' I got the same errors, except now I have now drivers installed at all! This is pushing me over the edge - Windows is looking ever more appealing. 

I just don't understand why it worked fine before, and now after a re-install of Breezy it's not working. I did nothing differently (that I am aware of anyway!). 

Anyone know how I FTP from the command line to re-download the 8756 Nvidia installers and I'll just follow the guide again but I need to be able to download it first via command line because X no longer works (I using another machine to write this)? 

Thanks

Ted

---

### Post by tseliot on 2006-06-06
sudo nano -w /etc/X11/xorg.conf

and set the driver to "nv" instead of "nvidia" in the Section Device of that file.

Then type:
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)


And you will have the graphical interface up and running again.

We'll figure out the problem with your card tomorrow.

Regards

---

### Post by Ted_Smith on 2006-06-07
today is a joyous day! It worked and I now have GLX running and I can play Americas Army again!

I'd love to know what I was doing wrong though. In the end, I rebooted, got the GUI back up as you stated, downloaded the driver again, went back to the command line and installed using the 'i' feature (no differently to yesterday mind you). This time, it all went though - no errors about kernal differences or anything. Rebooted, and here I am. 

So, thanks very much for the help, especially TSElliot and his wicked script. Added to my favourites! As I've alread said, your contribution to Ubuntu users is outstanding :-)

Bon soir.

Ted

---

### Post by ruimoura on 2006-06-13
I read today this post and i can understand one thing. How the hell do you play AA if they didn't lunch the 2.6 version for linux? I used to play AA on Linux when it was on 2.5 (better fps than on windows !!) but they left the development of the game for linux ... Do you play on wine? Cedega?

---

### Post by Ted_Smith on 2006-06-13
There are still a few 2.5 Linux servers running that we all play on, including the newly formed Ubuntu Special Forces clan ([http://usf.ahsclan.xmgfree.com](http://usf.ahsclan.xmgfree.com))

Ted

---

### Post by billybobjoe on 2007-03-26
I hope this thread may have some life to it...I am having the same problem running Americas Army 2.5.  I am rather new to Linux.  I have a biostar motherboard, an amd 3100+ athlon xp and an ati 700x pro video card.  I checked my fps and this is what I got:
10974 frames in 5.0 seconds = 2183.623 FPS
15277 frames in 5.0 seconds = 3051.160 FPS
15360 frames in 5.0 seconds = 3054.415 FPS
15361 frames in 5.0 seconds = 3051.945 FPS
14234 frames in 5.0 seconds = 2838.469 FPS
13246 frames in 5.0 seconds = 2631.432 FPS
14993 frames in 5.0 seconds = 2986.493 FPS
15040 frames in 5.0 seconds = 2991.656 FPS
14565 frames in 5.0 seconds = 2893.543 FPS
15062 frames in 5.0 seconds = 2998.240 FPS
14027 frames in 5.0 seconds = 2787.583 FPS
15034 frames in 5.0 seconds = 2997.103 FPS
10146 frames in 5.0 seconds = 2019.160 FPS
15221 frames in 5.0 seconds = 3030.749 FPS
15106 frames in 5.0 seconds = 3009.869 FPS
14987 frames in 5.0 seconds = 2993.928 FPS
13160 frames in 5.0 seconds = 2617.186 FPS
14727 frames in 5.0 seconds = 2929.500 FPS
15340 frames in 5.0 seconds = 3055.658 FPS
15253 frames in 5.0 seconds = 3032.616 FPS
15079 frames in 5.0 seconds = 3015.798 FPS
10371 frames in 5.0 seconds = 2056.465 FPS


Thanks.

---

### Post by merlyn on 2007-03-26
There are still 2.5 servers up and runnning?

Cool I'm off to do an install and get back into this on Linux.

I freely admit to playing the latest version on Win 2K from time to time but prefer where possible to do gaming in Linux.

Sooner or later, most likely later game developers will catch onto the fact that there is a Linux market, and that people would be willing to pay for quality titles on Linux.

Cheers.

---

