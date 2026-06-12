---
title: "Scorched 3d problems"
date: 2006-06-15
forum: Gaming &amp; Leisure
---

### Post by shendric on 2006-06-15
Hi all,

So, I tried installing scorched 3d on my Breezy box, by using alien on the 39.1 rpm.  It seemed like people had good experiences with it.  It installed no problem, but I get the following error:

Display:ERROR: Failed to set video mode.
Error Message: Couldn't find matching GLX visual
--------------
Requested Display Mode:-
Driver=x11
Resolution=640x480x0 (windowed)
DepthBuffer=24
DoubleBuffer=On
ColorComponentSize=0

Scorched 3D Display: ERROR: Failed to set the display mode.
Ensure that no other application is exclusively using the graphics hardware.
Ensure that the current desktop mode has at least 24 bits colour depth.

I've gone to my xorg.conf and checked to be sure that my display is set to 24 bit mode, and I've made sure that I've got the most recent versions of the nvidia drivers for my machine installed.  The NVIDIA logo comes up on boot up, like you expect, but I still get this error.  Others seem to have gotten Scorched3d to work, but I'm still having difficulty.  Does anyone have any ideas that I could try?

Sean

---

### Post by Footissimo on 2006-06-15
You know that its in the repos?  On Dapper its 39.1..not sure about Breezy

---

### Post by shendric on 2006-06-16
[QUOTE=Footissimo]You know that its in the repos?  On Dapper its 39.1..not sure about Breezy[/QUOTE]

Yup, that's where I got it to install.  Didn't seem to work, though.

Sean

---

### Post by shendric on 2006-06-17
[QUOTE=shendric]Yup, that's where I got it to install.  Didn't seem to work, though.

Sean[/QUOTE]

Sorry, I realize that must sound weird.  I first tried to install it from Synaptic, but when it didn't work, I decided to try and do an alien/rpm installation, using the latest version on the Scorched3D website.  So, I tried both, with the same results.

Would it help if I posted my xorg.conf?

Sean

---

### Post by shendric on 2006-06-21
*nudge*

I don't mean to be a pain, but I'm really hoping that I can get Scorched 3D to work on my Ubuntu box.  I'm willing to post my xorg.conf, if it would help.  I could try to uninstall Scorched 3D and reinstall it using Synaptic, although my first attempt at that installation had the same problem.

Sean

---

### Post by keithjr on 2006-06-21
heh, nothing wrong with a harmless little bump :)

Anyhow, is this the only game you've had trouble with?  It seems like from what it's saying, if this program were to have trouble setting the video modes you'd expect others too as well.

(edit)
I just installed it and it worked fine from synaptic.  I have ATI drivers so I can't really try to reproduce your problem, but we'll see

---

### Post by Footissimo on 2006-06-21
I know you said about the drivers, but have you checked with a:

```
glxinfo |grep direct
```

Just to check that direct rendering is working?  If it is then posting your xorg.conf may be a good idea..

---

### Post by shendric on 2006-06-25
[QUOTE=keithjr]heh, nothing wrong with a harmless little bump :)

Anyhow, is this the only game you've had trouble with?  It seems like from what it's saying, if this program were to have trouble setting the video modes you'd expect others too as well.
[/QUOTE]

At this point, it's the only game I've had trouble with, but I haven't really tried any others.  I can run 3d modeling software with no problem, and it runs fine, if that helps.

---

### Post by shendric on 2006-06-25
[QUOTE=Footissimo]I know you said about the drivers, but have you checked with a:

```
glxinfo |grep direct
```

Just to check that direct rendering is working?  If it is then posting your xorg.conf may be a good idea..[/QUOTE]

Here's what I get with a glxinfo command:

```

Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
... ad nauseum

```

I've seen some other folks with issues similar to this, but most of the solutions seem to hinge on installing the correct NVIDIA drivers, and I've checked this out numerous times.  So, I'm wondering what else could cause this.

Sean

---

### Post by keithjr on 2006-06-25
You might want to pick through your xorg.conf file and see what the display settings are.  Something is amiss.

---

### Post by shendric on 2006-06-25
[QUOTE=keithjr]You might want to pick through your xorg.conf file and see what the display settings are.  Something is amiss.[/QUOTE]

Here's what comes up in my xorg.conf regarding glx:

```

Section "Module"
#       Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
#       Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

```

And here's the device section:

```

Section "Device"
        Identifier      "NVIDIA"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP"                 "1"
#       Option          "TwinView"
#       Option          "TwinViewOrientation"   "DFP-0 RightOf CRT-0"
#       Option          "MetaModes"             "1680x1050, 1024x768; NULL, 1024x768; 1680x1050, NULL; 1680x1050 +0+0, 1024x768 +1024+0"
#       Option          "MetaModes"             "1024x768, 1680x1050; NULL, 1680x1050; 1024x768, NULL; 1024x768 +0+0, 1680x1050 +1024+0"
EndSection


```

Based on what I had heard, I thought this looked ok.  Am I incorrect, or is there some other part of the xorg.conf that I should be looking at?

Sean

---

### Post by Footissimo on 2006-06-26
Your Identifier under "Device" is unspecific (e.g. mine says "NVIDIA Corporation NV36.4 [GeForce FX 5700VE]") - just tried using a straight NVIDIA on my xorg and the X-server wouldn't load, so I wonder if that may be your problem.  You could use:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to reconfigure xorg, though if your computer blows up and takes your house, family and pets with it..don't blame me :)

Modules seem OK.  The other thing I thought about was if you were using new Nv drivers on an old (i.e. pre Nvidia 5 series..I think) card - if so you may need the old nvidia-glx-legacy drivers (from the repos) rather than the nvidia-glx drivers.

I may be talking out my arse here, so hopefully someone more technical will come along and correct me :)

---

### Post by keithjr on 2006-06-26
if his pets look anything like the cat in your sig, then I think it's for the best...:twisted: 


What is odd is that the errors your getting from glxinfo seem like you shouldn't be able to play ANY 3d games at all.  Do you get any response from glxgears?

---

### Post by shendric on 2006-06-26
[QUOTE=keithjr]
What is odd is that the errors your getting from glxinfo seem like you shouldn't be able to play ANY 3d games at all.  Do you get any response from glxgears?[/QUOTE]

Same error with glxgears.  

The graphics card is the following:

 PCI Express NVIDIA GeFORCE GO 6600
128 MB dedicated Video RAM
Accelerated OpenGL

That seems like a fairly new graphics card, so I'm guessing I don't need the legacy drivers, but maybe I'm wrong.

Sean

---

### Post by Footissimo on 2006-06-26
Nah you don't. I'd try changing the identifier via thing auto-xorg reconfigurer thingy.

> if his pets look anything like the cat in your sig, then I think it's for the best...

People are so mean.  Fluffkins is old and needed new teeth, so I got some dentures done for him.  He's got a good smile on him now.

---

### Post by shendric on 2006-06-26
[QUOTE=Footissimo]Nah you don't. I'd try changing the identifier via thing auto-xorg reconfigurer thingy.
[/QUOTE]

I'm assuming that's the sudo dpkg-reconfigure -phigh xserver-xorg thingy? :) 

What's the likelihood that things will go bad?  If I just make a backup copy of the xorg.conf, can I get things back to where they were before, in case something fritzes?

For the record, I like the cat's grin.  The dentist does good work.

Sean

---

### Post by Footissimo on 2006-06-26
Yeah, I'd definitely make a backup.```
sudo cp /etc/X11/xorg.conf /etc/X11/xorgmycomputerisabouttoblow.conf
``` should do it.

---

### Post by keithjr on 2006-06-26
I wish I could help more, but I'm an ATI user and don't have any experience in nVidia hardware drivers.  However, it is clear this problem isn't originating from Scorched 3d; it is coming from your video card (and/or its drivers).  I might recommend you post a thread relating to your GLX problems in the Video and Sound forum.  Provide the specs, the xorg info, and the error outputs.


that is, if the aforementioned solution doesn't work

---

### Post by Jasper Houtman on 2006-06-26
Am I the only one who noticed he has load "GLcore" and load "dri" disabled?
Impossible to run 3d games without them loaded, just remove the # before the entry.

---

### Post by shendric on 2006-06-26
Ah, well, I tried the dpkg-reconfigure, but it still didn't help.
Didn't blow up the computer, but it didn't solve the issue.  Thanks for the suggestions.  I'll post this to the Video and Sound forum.

Appreciate it, guys.

Sean

---

### Post by Footissimo on 2006-06-26
[QUOTE=Jasper Houtman]Am I the only one who noticed he has load "GLcore" and load "dri" disabled?
Impossible to run 3d games without them loaded, just remove the # before the entry.[/QUOTE]

You can disable both of them..and its recommended to do so when installing Nvidia drivers manually..just as long as the 'glx' module isn't commented out.

---

### Post by Jasper Houtman on 2006-06-26
OK, sorry.
That explains why noone mentioned it.

---

### Post by shendric on 2006-06-26
[QUOTE=Jasper Houtman]Am I the only one who noticed he has load "GLcore" and load "dri" disabled?
Impossible to run 3d games without them loaded, just remove the # before the entry.[/QUOTE]

What I've been given to understand from all that I've seen regarding NVIDIA drivers is that those both have to be commented out.  I'm not sure why, but that's a pretty common thread.

I suppose I could try uncommenting those to see what happens, though.

Sean

Sorry, just realized that I posted that after someone already responded.

---

### Post by Footissimo on 2006-06-26
[QUOTE=shendric]Ah, well, I tried the dpkg-reconfigure, but it still didn't help.
Didn't blow up the computer, but it didn't solve the issue.  Thanks for the suggestions.  I'll post this to the Video and Sound forum.

Appreciate it, guys.

Sean[/QUOTE]

Sorry couldn't be more help :(  I do have a feeling it may be the identifier, but good luck anyway :)  Like Keith says, it's definately a driver / xorg issue

---

