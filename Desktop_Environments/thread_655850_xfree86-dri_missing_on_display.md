---
title: "xfree86-dri missing on display"
date: 2008-01-01
forum: Desktop Environments
---

### Post by onthefritz on 2008-01-01
Well first with the details.

Graphics card: Radeon 9700 Pro
Distor version: Ubuntu 7.10
Kernel version: 2.6.22
ATI restricted Drivers: Installed (Installed by Ubuntu...not the ATI distributed driver.)

I get this error whenever I try to run 3d accelerated programs. Here is the output from many of the programs I try to run:

```

Neverwinter Nights:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

glxgears:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0

```

I have tried to install the ATI drivers from their site but all my graphics slowed to a crawl. So that was a bust. I have tried many a few other idea on other sites with no fix... does anyone else have an ideas?

Thank you

OTF

---

### Post by Ziggy114 on 2008-01-17
Same problem here, with the same or at least very similar setup:

Graphics: ATI Radeon 9700 Pro
Distro: Ubuntu 7.10
3.2 GHz P4 on ASUS P4P800 Deluxe w/ 2.5 GB RAM

I can't run glxgears at all - the one time I did it took me back to the login screen as if I'd just rebooted.

Entering ```
glxinfo | grep 'direct rendering'
``` returns 
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```
I take this to mean that OpenGL is completely out of the question.

After initially installing Ubuntu and while using the default (non-restricted) graphics driver everything seemed fine, but my desktop would occasionally lock-up... I could still move my mouse cursor, but nothing would be clickable. No doubt this was the graphics card not playing nice, but due to *another* [bug]("http://ubuntuforums.org/showthread.php?t=582962") I had no virtual terminals available to check if this was true or not. I've only had the computer lock up on me once since switching to the restricted drivers and following all of those '[get compiz fusion working]("http://ubuntuforums.org/showthread.php?t=569654")' forum threads. I haven't tried installing the ATI distributed drivers yet, nor do I think that I will.

What gives? I wish ATI would quit dragging their feet and release a decent Linux driver for once.

---

### Post by onthefritz on 2008-01-18
When I installed the ATI distributed ones they slowed my system down so bad I couldn't do anything. This is the workaround I am using until ATI comes out with new drivers. 

Before running a 3D program, other than compiz, open a terminal and run this command.
```
export DISPLAY=:0.0
```

I'm not sure why this works. I read the reason somewhere but I forgot! lol. If I find the thread again I'll post it up here.

OnTheFritz

---

