---
title: "FreeOrion: OpenGL 2.0 requirement"
date: 2009-07-14
forum: Gaming &amp; Leisure
---

### Post by The Question on 2009-07-14
How do I meet this requirement?  The game tells me my GL version is 1.3 Mesa 7.4.  I have an ATI Radeon Xpress 200 (pretty old) and AMD's website (and the ATI wiki) says I can only run their Catalyst driver v.9.3 with that card which is not compatible with Ubuntu 9.04.

So is there another free driver I could try or is it time to get a new graphics card?

---

### Post by oldrocker99 on 2009-07-14
Oh, is it EVER time to get a new graphics card. And DEFINITELY not an ATI card. nVidia's drivers haven't abandoned chips that are still on store shelves, as ATI has (by the way, those driver woes we are experiencing are also felt by Mac and Windows users, as well](*,)).

I have been an AMD/ATI user for over a decade, and they're never going to get another cent from me.

:guitar:

---

### Post by lukeiamyourfather on 2009-07-14
There's nothing wrong with that graphics chipset, built on the motherboard I assume? Its not new but it'll still work. There are open source drivers that will support that chipset so no need to use the proprietary drivers and the open source drivers even have OpenGL support.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Upgrading to a newer card is not a bad idea if you can spare the change but not necessary. Also don't think that ATi cards are any better or worse for Linux than nVidia cards because both have had issues with Linux for years and will both continue to have hit and miss official support for new Linux releases. Cheers!

---

### Post by The Question on 2009-07-15
Ok, I looked at that website, but it seems to be mostly for people that are using fglrx and want to switch to the "ati" driver.  I have not installed fglrx so am I not using the "ati" driver by default?  Hardware Drivers tells me I am not using any proprietary drivers.  Is there a command to check which driver you are using?
  
When I run the commands under Testing the Driver section, it is already listed as SGI / Direct Rendering on.

If I am indeed using the "ati" driver then the problem is that this driver does not support OpenGL 2.0.

---

### Post by PrimoTurbo on 2009-07-15
You really need a propriety driver to play games in 3d on Linux.

---

