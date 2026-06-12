---
title: "Compiz/Twinview + 3 monitors"
date: 2012-01-29
forum: Desktop Environments
---

### Post by kragebein on 2012-01-29
Hello.
I am trying to get compiz to work with 3 monitors. 

The following setups have been tried.

2 screens, twinview + 1 extra gnome session. [compiz works].
3 seperate gnome sessions, no twinview         [compiz works].
1 gnome session + 2 sceens twinview.            [compiz works].
3 seperate gnome sessions, Xinerama            [compiz does not work].

I am pretty decent with linux, and are currently running 10.04. What I am asking here is pretty advanced. 
I am looking for the Xinerama patch that allows me to run Xinerama together with Compiz with the use of xserver-xgl. 
and preferrably a HOWTO along with that..

Does anyone know?

My Goal is: 3 screens, xinerama with compiz.

I have 2 x nVidia 560TI

---

### Post by kragebein on 2012-01-31
Just in case anyone need help for this aswell, i found a solution that works for me.

--base-mosaic.

I removed my xorg.conf and ran this command in terminal as root:

```
nvidia-xconfig --base-mosaic --metamodes="GPU-0.DFP-0: 1920x1200+0+0, GPU-0.DFP-1: 1920x1200+1920+0, GPU-1.DFP-0: 1920x1200+3840+0"

```
You may need to alter DFP to what you need.
You get that information using 
```

nvidia-xconfig --query-gpu-info

```

I am using 2xGTX 560ti cards, with the 290.10 nvidia driver.

Good luck.

---

### Post by DrewDahl on 2012-02-17
Just thought I'd ask, but how's the 2D/3D performance with this setup?  Or, I suppose usability in general.

I'm currently running an AMD 5870 with three monitors and am in the process of putting together a new rig.  Just debating between going the nVidia route or sticking with AMD.

Thanks!

---

### Post by devout on 2012-09-11
> **DrewDahl said:**
> Just thought I'd ask, but how's the 2D/3D performance with this setup?  Or, I suppose usability in general.

I'm currently running an AMD 5870 with three monitors and am in the process of putting together a new rig.  Just debating between going the nVidia route or sticking with AMD.

Thanks!

Is that the same card as this?
[http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-5000/hd-5870/Pages/ati-radeon-hd-5870-overview.aspx](http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-5000/hd-5870/Pages/ati-radeon-hd-5870-overview.aspx)
What version of ubuntu are you running it with?
And that's 3 monitors at 2560x1440 via dvi dual-link?
Are you using 2 of the dvi ports and the DisplayPort?
If yes, are you using an active DisplayLink to dvi dual-link adapter?

---

### Post by DrewDahl on 2012-09-11
> **devout said:**
> Is that the same card as this?
[http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-5000/hd-5870/Pages/ati-radeon-hd-5870-overview.aspx](http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-5000/hd-5870/Pages/ati-radeon-hd-5870-overview.aspx)
What version of ubuntu are you running it with?
And that's 3 monitors at 2560x1440 via dvi dual-link?
Are you using 2 of the dvi ports and the DisplayPort?
If yes, are you using an active DisplayLink to dvi dual-link adapter?

Same Card? Basically.  It's the same chip on an HIS card.

I've 3 monitors: 2 @ 1600x1200 (rotated 90*, so 1200x1600) and 1 @ 2560x1600

The 2560x1600 (center) is hooked up to an Active DisplayPort to DVI Dual-Link Adapter, like you mentioned.  The other two (left and right @ 1200x1600) are being used with DVI cables.

I'm not running Ubuntu (although, there's no reason it wouldn't work on Ubuntu... Linux is Linux) -- I'm running Fedora, just to note.

This setup works for me using the 'xrandr' command and open source drivers.  With my setup, I just have KDE run a script that tells xrandr what to do once I log in. -- It'll also work with the proprietary ATI 'fglrx' drivers, if you choose to install those.  The ATI drivers provide a nice GUI and there's no need to fumble around with scripts as I have. (My reasoning was that of the kernel being updated before proprietary drivers were built for it, thus I would update my system, only to come back to not having the necessary module installed.)

Also, I don't have Compiz or anything like that setup, nor do I plan to.  I can play Nexuiz (3D FPS) without any issue though, so I don't imagine there'd be an issue w/ Compiz and 3D Acceleration.  If you plan to use the 3D acceleration at all though, I'd recommend the proprietary drivers.

---

### Post by devout on 2012-09-11
Ok, I was looking at the Nvidia Quadro NVS 450 after reading this post [http://forums.whirlpool.net.au/archive/1748751](http://forums.whirlpool.net.au/archive/1748751)
What's strange though, is that Leadtek have spoken to NVidia and reported back that using active dvi dual-link to DisplayPort definitely won't work.
I'm a bit confused about that, as it kind of looks from that post and some others I've read that it should work.
I don't need compiz, this machine will only be for development and playing with techy stuff. No gaming.
I'm also looking at the possibility of setting up 2 Gigabyte GV-N56GOC-1GI GTX 560 cards with SLI, but they take so much case room.
I also don't know for sure if they'd work. Although looks like kragebein got his working?
The Gigabyte GV-N56GOC-1GI GTX 560 cards may work with an active dvi dual-link to mini DisplayPort, but again, not sure.

Can't find any AMD 5870 for sale either.

In looking at the 6870, it looks like one of the dvi out's is dual-link.
So if using hi res monitors (above 1,920 x 1,200) one would have to use both mini DisplayPorts with active adaptors and the dvi dual-link port.

---

