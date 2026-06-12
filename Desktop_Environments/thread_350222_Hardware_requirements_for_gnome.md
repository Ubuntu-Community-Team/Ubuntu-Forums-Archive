---
title: "Hardware requirements for gnome?"
date: 2007-01-31
forum: Desktop Environments
---

### Post by ghandi69_ on 2007-01-31
High guys, I've had gnome running for a couple days and find it to be pretty sluggish with just a generic 6.10 install.  

I am running a Athlon 3200+Fx64, with 1 gig of ram and an Nvidia 7600GS.  I do know that I have the correct Nvidia drivers.

Is this not enough to have gnome running at a decent speed, or are there some useful tweaks out there that could speed things up for me?

---

### Post by isecore on 2007-03-25
I feel the same way. Gnome is running very sluggish, even though everything seemingly runs fast.

I've got plenty of RAM in my machine (1 gig), latest nvidia-drivers and everything is fine, yet navigating folders in Nautilus is almost painfully slow. I know that a lot of people say Gnome is sluggish and slow, but does it have to be this slow?

Navigating through my harddrive it takes about 1-2 seconds to open subdirectories. Always this sluggish feeling. This cannot be related to my computer, since there are no spikes i CPU-usage when doing this - just Nautilus being unnecessary sluggish and slow.

Is there anything I'm missing? I come from a serverside-perspective of Linux so most of Gnome and the desktop is pretty new to me.

---

### Post by jem7v on 2007-03-25
Those system specs Should be sufficient, I would think... I get roughly the same performance with a 750mhz Duron and 384 megs RAM.

---

### Post by isecore on 2007-03-25
> **jem7v said:**
> Those system specs Should be sufficient, I would think... I get roughly the same performance with a 750mhz Duron and 384 megs RAM.

Yeah, I'm running an AthlonXP 2200+ with a gig of RAM, so I really don't think it's slow hardware. Just Gnome/Nautilus lagging behind for whatever reason.

I've done all the optimization I can think of (prelinking, disabling IPV6 and such) but still Nautilus is annoying with the speed (or rather, the lack thereof). Haven't seen any solid tips & tricks for speeding up Nautilus though :(

EDIT: I googled and found [this page]("http://ubuntu-tutorials.com/2007/03/05/how-to-speed-up-the-nautilus-file-browser/") which suggests disabling as much previews as you can tolerate, but it did absolutely nothing to speed up my Nautilus. Turning off previews, thumbnails, everything - still 1-2 seconds to open a folder and a very sluggish feeling.

---

### Post by mgmiller on 2007-03-26
I have read this from other posters as well.  I have a 3200+ AMD 64 with 2 gig of ram and for the most part nautilus is very snappy unless the folder has  a lot of entries with thumbnail images.  For example, I have 1 folder with over 600 files all of which require a thumbnail image to be generated.  This can take upwards of 6-7 seconds to display.  If I change the view in the window to icon view instead of thumbnail view it opens almost instantly.  Otherwise, all my menus and other Gnome navigation items are very quick.  At least as quick or quicker than the 6 or so Windows XP machines I use at work.  I recently upgraded from a Geforce 6800 128 MB video card  to a Geforce 7800GT 256 MB but that didn't seem to affect anything in Gnome (UT2K4 was another story)  One thing to consider is if you have Beagle installed.  The Beagle front end seems to gum up a lot of things in Gnome.  I don't use it.  The deskbar applet is very happy without it and works instantly.  There is no waiting days/weeks for some database to populate.  The libbeagle0 package is a standard component of Ubuntu,  and it does not play well with the beagle package, which depends on it.  Weird, but you could try completely uninstalling the beagle front end and restart x and see what happens.

---

### Post by mgmiller on 2007-03-26
One other tweak I just thought of.  I am using the nvidia driver from the Ubuntu repos, (8776), not the one from Nvidia directly.  I found that I needed to add 1 line to my xorg.conf to speed up my 3d stuff a fair amount.

In the nvidia driver section of etc/X11/xorg.conf   I added the following line:

```
Option "NvAgp" "2"
```

This tells the driver to use agpgart instead of nvagp.  This boosted my frame rates in glxgears (I know it's not a benchmark)  from about 4000 fps to over 10,000.

All the choices for this line and their meanings are as follows:

Option "NvAgp" "1" ... use NVAGP, if possible
Option "NvAgp" "2" ... use AGPGART, if possible
Option "NvAGP" "3" ... try AGPGART; if that fails, try NVAGP

You can easily try different ones and restart x to see what effect it has.

---

### Post by NJC on 2007-04-17
I'm using Ubuntu 6.06 on a PIII/500Mhz w/ 640mb mem and I also have the "Molasses Syndrome." Even after everything is well cached the screen is laggy. Essentially all programs are culpable with the exception of Audacity. Scrolling through the Audacity directory structure is BAM lightning quick. No lag whatsoever. 

Not sure what to think of why Audacity would perform well??

The only solution I can think of is improving the video.

---

### Post by isecore on 2007-04-20
I just upgraded from Edgy to Feisty earlier today, and Nautilus seems to be A LOT more snappy now. It seems that the devs have worked hard on improving its browser speed, and that's great. So, an upgrade might do the trick for you guys.

---

