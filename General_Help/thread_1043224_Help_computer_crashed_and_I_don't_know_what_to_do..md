---
title: "Help: computer crashed and I don't know what to do..."
date: 2009-01-18
forum: General Help
---

### Post by stefangr1 on 2009-01-18
I just got three old unused computers from a hostpital for free, which I want to donate to a local youth club.

Specs:
Pentium 4, 1,6Ghz
256MB RAM
PCI ATI VGA Adapter
40GB IDE harddisk
LAN
No operating system and no cd/dvd player

I used my pxe-server and the Ubuntu 8.04LTS alternate installer to put an operating system on them. This runs amazingly fast, actually faster then I expected. Then I installed about any game that is in the repositories.

However, games with fast graphics (like Torcs and Flightgear) run at a very low framerate, while Flightgear even completely crashed the computer before I could do anything. The problem is that I have no idea what sort of graphics card the computers have (only that's ATI).

What should I do?

---

### Post by LoneWolfJack on 2009-01-18
Did you install the restricted drivers?

---

### Post by stefangr1 on 2009-01-18
> **LoneWolfJack said:**
> Did you install the restricted drivers?

I did install the "ATI Catalyst™ 8.12 Proprietary Linux x86 Display Driver", but after I did that I got a message that the display could not be detected, and the computer had to enter low graphics mode.

Quote from an Ubuntu howto: "The 'fglrx' driver does not support cards earlier than the 9500".
Well, I don't know how old these cards are (or what type), but they're probably not much.

---

### Post by abn91c on 2009-01-18
you may want to install the edubuntu desktop for educational games for kids or the just the gcompris package by it self with the appropriate language pack for your country.
use this to get your video card model```
sudo lshw -C video
```

---

### Post by stefangr1 on 2009-01-18
OK, we're coming a bit further: 
ATI Technologies Inc. Rage 128 Pro Ultra TF.

---

### Post by abn91c on 2009-01-18
> **stefangr1 said:**
> OK, we're coming a bit further: 
ATI Technologies Inc. Rage 128 Pro Ultra TF.
 I have that same video card, compiz will not work with this model, flash games will be ok after you install the plug-ins
try this game after you install flash to test it [http://n.ethz.ch/student/mkos/pinguin.swf](http://n.ethz.ch/student/mkos/pinguin.swf)
click on yeti to drop penguis, click on yeti again to smack the penguis :-)

---

### Post by stefangr1 on 2009-01-18
I have actually installed the Gcompris package btw., but the kids over there are in the 12-15 range, so I think they'd like racing, flying, etc.

---

### Post by abn91c on 2009-01-18
I'm using Kubuntu but if you search for **racer** or **racing** in synaptic you will get quite a few racining type games to install

---

### Post by stefangr1 on 2009-01-18
Well, thats another thing they don't have internet. I could connect the computers off caurse, so that they can play against each others. Otherwise they could play online flash games.

It appears (I'm googling around a bit in the mean time) that there is a linux driver around somewhere, called r128. My computer isn't using it, according to my xorg.conf, and I haven't found a place where I can't download the driver.

---

### Post by stefangr1 on 2009-01-18
> **abn91c said:**
> I'm using Kubuntu but if you search for **racer** or **racing** in synaptic you will get quite a few racining type games to install

I know, I installed several from the repositories. However, something is wrong with the graphics and I don't know yet how to solve it...

---

### Post by abn91c on 2009-01-18
have you looked at this thread  [http://ubuntuforums.org/showthread.php?t=948091&highlight=ati+rage+128](http://ubuntuforums.org/showthread.php?t=948091&highlight=ati+rage+128)

---

### Post by stefangr1 on 2009-01-18
> **abn91c said:**
> have you looked at this thread  [http://ubuntuforums.org/showthread.php?t=948091&highlight=ati+rage+128](http://ubuntuforums.org/showthread.php?t=948091&highlight=ati+rage+128)

I just did, however, there doesn't appear to be a solution over there, and that person's problem seems to be worse. Thanks for looking into it though, and for the suggestion.

In the mean time I have been playing around with debian packages, and it seems that X is now using the dedicated r128 driver, in stead of the build in one. So I though for a sec: yippee!

However, the fast graphics games now stopped working entirely, with error:
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Sys_error: GLimp_Init() - Could not load OpenGL subsystem

---

### Post by stefangr1 on 2009-01-18
Can I just include:

Section "Module"
    Load           "glx"
EndSection

in my xorg.conf? Or do I have to install something for that first...

---

### Post by stefangr1 on 2009-01-18
Reverting back to the old xorg.conf didn't work. And somewhere in the process of installing the r128 driver something odd came up: the "up"-arrow has now become print screen and some other keys also function weird (ctrl+alt+backspace doesn't work anymore).

So it seems that I'm going to do a second reinstall...

Then there's what appears to be another stupid problem: System Resque CD won't load from the PXE server due to a vague "timed out" error, which means that I'll have to install the computers one by one.

---

