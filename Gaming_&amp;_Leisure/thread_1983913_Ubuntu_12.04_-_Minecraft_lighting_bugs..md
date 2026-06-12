---
title: "Ubuntu 12.04 - Minecraft lighting bugs."
date: 2012-05-21
forum: Gaming &amp; Leisure
---

### Post by AnonymousJustified on 2012-05-21
So, I got Minecraft running on Ubuntu, and on the surface it seems lovely. Runs just fine, and faster to boot!

But, the issue really arises immediately after I enter a cave/building/anything with a roof. The lighting starts getting all weird inside, and, when the light levels are low enough, blocks even become completely invisible.

I suspect that this has to do with the lwjgl files I had to manually update to get Minecraft running properly, which'd explain why Mojang hasn't switched to the newer files yet.

Does anybody know a fix, such as an older version of lwjgl that still works on Ubuntu 12.04? Thanks in advance! :3

---

### Post by mode7 on 2012-05-21
Can you show a picture?

I get this weird glitch, probably not related, where my lighting never seems to update. Torches are sitting there, but they don't light anything until I set another light source nearby.
Also, I can walk right into a cave, and it will be nearly pitch black, and after about 5 seconds or so, the light will finally update.

---

### Post by ELD on 2012-05-21
I don't think it's directly an issue with the game library i think it's a server side thing too.
 
I've seen a big post on the minecraft reddit with someone complaining about it, apparently it's a server issue? I'm not really sure but i get it now and then too, no more or less since Ubuntu 12.04 it's always been an issue on Windows as well.

---

### Post by regor210 on 2012-05-21
I had and old Dell office computer. A P4 no APG with integrated Intel graphics. It was doing the look up to see invisible blocks thing.

I tried the newest version of &#65279;lwjgl and a lot of other fixes as well like ubuntu-x-swat and xorg-edgers. 

I think if I had a newer graphics adapter, an updated video driver would have fix it but with hardware that old I considered my self lucky it worked at all.  

You can check to see whats going on with your video drivers.

Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window one line at a time minus the $.

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.

---

### Post by AnonymousJustified on 2012-05-22
> **regor210 said:**
> Open a terminal, press ctrl+alt+t all at the same time. Cut and paste the following commands into the terminal window one line at a time minus the $.

#video card and driver information
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.

```
Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	82865G Integrated Graphics Controller
SVendor:	Dell
SDevice:	Device 0151
Rev:	02
Driver:	i915
Module:	intelfb
Module:	i915

```

Also, to answer ELD, I prefer playing SSP. So, it's not server side, as there is no server.

---

### Post by regor210 on 2012-05-22
1st thing I would try is, get into your BIOS and make as much ram or memory available to your i915 video adapter as you can.

With Ubuntu 12.04 having just come out I don’t know if x-swat will help. x-swat has the newest somewhat  stable drivers for Intel graphic adapters. xorg-edgers has the testing  Intel graphic drivers and may may crash your desktop with every new update. 

If you would like to try x-swat heres how
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

$ sudo apt-get update
$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade

---

### Post by RTimz on 2012-05-22
I've had the same thing, although other people om [[COLOR=black]Minecraft Members[/COLOR]]("http://MinecraftMembers.com") seem to be fine running a much higher spec than I have :mad:.
 
Anyone have any success fixing it?

---

