---
title: "need bargain AGP vid card for compiz-fusion"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by maestrobwh1 on 2007-08-12
I am looking for a bargain AGP card that works well with fusion that hopefully has video out. I use a projector at work with my own "portable" desktop unit with Kubuntu Feisty installed... and would rather just plug in a simple video or s-video cable into the card so I don't have to configure xorg for different resolutions. 

Currently, the motherboard has integrated sis graphics so I haven't bothered installing Compiz-Fusion, which at least in my laptop is a no go at this point.

My high school students are relatively impressed (well, not really, but kind, of sort of...) with the fact that I use Linux, so adding the flair I get on my home desktop using Compiz-Fusion with even my lowly ati radeon 7200 card, might be somewhat impressive to them.

I understand that ati isn't usually that stable with compiz yet, so perhaps a nvidia? I had to add some tweaks in my xorg file to stabilize Compiz with it.

---

### Post by Onay on 2007-08-12
I just bought an Nvidia GeForce 6200 with 256MB DDR2 memory at TigerDirect for only $44.99. Great deal for that kind of card, and all ubuntu effects on Beryl have been smooth and silk.

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1776106&CatId=935](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1776106&CatId=935)

---

### Post by psyopper on 2007-08-13
I'll second the vote for the 6200, It's almost seamless, a little laggy with serious stuff like rotating a transparent cube, or rotating a cube with 3D windows.

---

### Post by maestrobwh1 on 2007-08-13
Need some help before I do this:-)

Okay, so currently, I am using the integrated sis graphics.  I'll backup my xorg.conf file.  When I install the new card, I should probably boot into recovery mode... then from there, run

dpkg something something xserver-xorg...

---

### Post by psyopper on 2007-08-13
Actually, it's even easier than that. Sort of.

You can boot with the vesa driver in the xorg.conf:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

sudo gedit /etc/X11/xorg.conf

```

In the device section change the Driver to "vesa" without the quotes.

Then go to System - Administration - Restricted Drivers Manager and tell it you want to use the Nvidia driver and let it do it's thing. When it asks you to reboot, reboot and you *should* be OK.

---

### Post by maestrobwh1 on 2007-08-14
Someone actually gave me a Nvidia geforce mx 440 64 MB AGP yesterday... for free and it is supposed to work.  Will the method you mentioned above work just to get it working overall, and does the proprietary driver work with Compiz to your knowledge?

I know 64 MB isn't a lot, but my home computer has an ATi radeon 7200 and runs everything quite nicely.  I am not a gamer and won't be using the new machine for much other than a presentation station at work.

---

### Post by psyopper on 2007-08-14
It should work, Restricted Drivers Manager, I believe, has driver for this card in nvidia-glx (rather than nvidia-glx-new which covers the GF5-GF7). 

It *should* be the same process as well. In fact you might not even need to make any precursor changes to the xorg.conf either. X might realize that you are not using the integrated video and automatically put you into vesa. It may not.

One thing to be sure of - after you put the new card in go into your computer BIOS and ensure that you disable the onboard graphics card. 

If X pukes when you try to restart just pull out the new card, reconnect your monitor to the old card, reenable the old card in the BIOS, then follow the directions I outlined previously.

One thing for sure will be that you won't get the performance in Compiz from the MX that you would get with the 6200 referenced in this post. I'm not even positive that you will be able to run Compiz on the MX at all. There's only one way to find out.

---

### Post by VictorR on 2007-08-14
I use NVidia GeForce4 MX440 with 64 MB memory, Compiz Fusion runs perfectly. The driver is usual from Ubuntu repository nvidia-glx (neither "legacy" nor "new"). First change your video mode to Vesa as suggested above, restart with new hardware, then follow HowTo installing compiz with nvidia. It must me all right.

---

### Post by maestrobwh1 on 2007-08-15
You are all the best!  I'll post back with my results:-)

---

