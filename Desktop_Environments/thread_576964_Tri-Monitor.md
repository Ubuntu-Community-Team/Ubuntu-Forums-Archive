---
title: "Tri-Monitor"
date: 2007-10-15
forum: Desktop Environments
---

### Post by SuperSam on 2007-10-15
Hi all.

After some long working hours and some bargaining with people I have managed to aquire for myself three monitors :)! Now, I have this running beautifully on Windows XP, and prior, ran pretty sloppy on Vista. Being a Linux user and maintainer of Linux servers I am somewhat fluent in Linux talk so don't be afraid to use the longer words when helping me!

I have the monitors on 2 different levels and they are different monitors too. My left and right monitors are GNR F173, 17" 1280x1024 4:3 flatscreens. My middle screen is an Acer AL1916W 1440x900 16:10 widescreen.

[http://www.nitrousirc.net/3mon.JPG](http://www.nitrousirc.net/3mon.JPG)
[http://www.nitrousirc.net/3monpic.JPG](http://www.nitrousirc.net/3monpic.JPG)

This is how my computer desktop looks. I have had trouble having to change and reinstall drivers, as well as manually editing the X11/xorg.conf file to my own resolution and refresh rate when I ran just a single 16:10 monitor when Ubuntu 7 first came out. I was wondering firstly, is it possible, and secondly, is it hard and time consuming to set up these desktops the same as I have on Windows XP?

My System Specs (which I will use on Ubuntu will be) as follows:

AMD Opteron Dual-Core 175
Crucial Ballistix Tracer DDR500 PC4000 RAM
DFI Lanparty Crossfire S939
120GB ATA/133 7200RPM WD Hard Drive
* 2 x nVidia 7600GT (NOT IN SLI OR LINKED IN ANY WAY)

I hope I have been enough of a help in explaining so that you can help me.

Many thanks in advance,

SuperSam!

---

### Post by specvthis on 2007-10-16
Well to start do you have the nvidia drivers installed?  They have a command line xorg.conf editing tool that would probably help a lot.  After installing the drivers (Restricted Drivers Manager) run 'nvidia-xconfig -A' in a terminal to start.  Tons of options.  Looks like you would need multigpu with and a dualhead setup.

---

### Post by SuperSam on 2007-10-16
I haven't actually installed Ubuntu yet... I was going to do it if I found out it wasn't too difficult to do then I was going to install it, however I will be installing later today, probably around 3pm (UK Time).

---

### Post by Joeb454 on 2007-10-16
Also, you might find that you'd be better off linking the cards via SLI.

Having said that I've never had 2 gfx cards in at once :p I know you can run 2 monitors off 1 card, because I've done that

---

### Post by SuperSam on 2007-10-16
I can't link the graphics cards in SLI as I have an ATi Crossfire board. Linking the cards in SLi has no effect on being able to support more monitors, I already have 3 running in XP fine without any SLi running.

---

