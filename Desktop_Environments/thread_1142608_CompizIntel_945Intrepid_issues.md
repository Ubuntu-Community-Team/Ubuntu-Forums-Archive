---
title: "Compiz/Intel 945/Intrepid issues"
date: 2009-04-29
forum: Desktop Environments
---

### Post by Nafsten on 2009-04-29
Hi,

I've been fighting this for a little while, and still not got anywhere:

When I first installed Ubuntu (Hardy) a while ago, Compiz worked a charm.  However, I intalled xscreensaver, which seemed to break it.  Even after getting rid of xscreensaver I still got nowhere, so I pretty much just gave up.

Recently I updated to Intrepid, and while playing with something else I removed my xorg.conf, and Compiz started working again.  However, it has again stopped, as I (forgetting what happened last time) installed xscreensaver again.  It's gone now, but the problem remains!

> When I run compiz --replace, I get this output:
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

I guess the important one is the lack of a 'PCI ID for VGA'.  If I run compiz-check, the only failing point is that there is a software rasterizer.  

If anyone has any suggestions, that'd be awesome.  I can get various other outputs if necessary

---

### Post by andrea000 on 2009-04-30
post your xorg file 

applications -> accessories -> terminal
then type in 

sudo vi /etc/X11/xorg.conf 

copy the output and post that back

---

### Post by Nafsten on 2009-04-30
> **andrea000 said:**
> post your xorg file 

applications -> accessories -> terminal
then type in 

sudo vi /etc/X11/xorg.conf 

copy the output and post that back

Thanks for the response - I mentioned in my post that I'm not actually using xorg.conf, and instead relying on everything being autodetected. (Works pretty well so far!)

However, I have now managed to solve it by following these steps:
completely remove the intel drivers
restart X in VESA mode
install the drivers again
restart X

I'd tried removing them before, but not including all config, and there seemed to be some other config that messed it up.

Now I've just got to find an alternative to xscreensaver that doesn't break compiz again

---

