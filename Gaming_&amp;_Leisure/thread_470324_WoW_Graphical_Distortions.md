---
title: "WoW Graphical Distortions"
date: 2007-06-10
forum: Gaming &amp; Leisure
---

### Post by onimike on 2007-06-10
System Specs:

Ubuntu Feisty (7.04)
Wine: Latest, from this page: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Ram: 1g
CPU: 3ghz
Video:  Onboard..  can't upgrade further without buying a new mobo

I've installed WoW, and through many errors and crashes managed to get all the latest patches.

One problem I do have is I cannot run WoW in d3d mode, it hardlocks after hitting the second "Accept" button for the Terms of Use.

Anyway my main problem here is I finally manage to get to the character creation screen, and all of the races graphical representations are horribly distorted, heres an example:
[http://img394.imageshack.us/img394/9692/screenshotty3.png](http://img394.imageshack.us/img394/9692/screenshotty3.png)

This is probably due to my video card, but is there anything short of upgrading my mobo (to use something better than regular pci slot) to fix this?  With d3d mode crashing I don't know if I can edit any graphical settings.

Here's my Config.wtf:
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxWindow "1"
SET gxResolution "1024x768"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "400.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET accountName "endroc"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET realmName "Duskwood"

Thanks for any help.

---

### Post by Motoxrdude on 2007-06-10
I had that same problem just yestarday. I had to run WoW using crossover office to get past the terms of use. Sorry i can't really help you out though.

---

### Post by hikaricore on 2007-06-10
That looks like a classic intel onboard + crappy drivers, screenshot.  >,<

---

### Post by onimike on 2007-06-10
Well, I do have this old and useless Geforce FX 5500 PCI, since my mobo can only use PCI slots... but it makes a horrible grinding noise so I took it out :|

Gateway blows.

---

### Post by Motoxrdude on 2007-06-10
It's not your drivers, i can garuntee that. I had the exact problem using a x800GTO. Or could it be the drivers? not sure, but doubt it.
try
> wine wow/directory -opengl
and see if that turns up any new results.

---

### Post by onimike on 2007-06-11
No luck with that either :(

I tried entering a world reguardless of it but hardlocked again.

Oh well... Probably the only thing I can do is upgrade hardware.

---

