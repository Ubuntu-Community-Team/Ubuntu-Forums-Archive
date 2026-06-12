---
title: "xorg-reconfigure isn't giving me any reconfiguring options!"
date: 2009-06-09
forum: General Help
---

### Post by jonboy99 on 2009-06-09
Hi folks, forgive any spelling mistakes etc as I am writing this on a 640 by 480 screen!
I am trying to install the mesa driver or in fact any driver (not too fussed about 3d at the moment) for my nvidia card.  It is the new gtx 275 so has only been out a month.  
When I boot up in ubuntu the max res is only 640 by 480.  I have tried the usual 
sudo dpkg-reconfigure xserver-xorg

But this only gives me options to reconfigure the keyboard.  I only dabble under the hood of ubuntu occasionally but a couple of years ago when I first started I was able with the same command to choose the driver (mesa, nv etc).  I have also looked in xorg.conf and can't find any of the old information about where the driver might be configured - just 'configured display driver' - well, where is the info about how it is configured??

I have tried envy but the drivers installable through envy are too old to support this card, however I know I can get full resolution as when I uninstalled envy I got full res with (it think) the mesa driver in use, however I can't get it back!
Manual install of the latest nvidia linux driver just won't work, I get the same low res - so I want to use the mesa or nv driver or something similar which will give me full res.

So how do I get all the xorg config options?

Thanks
Jon

---

### Post by jonboy99 on 2009-06-09
Fixed using this page [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

I put this in the xorg.conf file and commented out the existing device section.

Section "Device"
  Identifier  "Card0"
  BoardName   "Generic Geforce GTX275"
  Driver      "nv"
EndSection



However there really should be some option when reconfiguring the x server to configure these settings without having to manually edit the xorg.conf file I would have thought.

---

### Post by Yellow Pasque on 2009-06-09
I doubt either the nv or nouveau driver has support for this card yet. You're stuck with VESA until Nvidia releases a proper driver for it.

---

### Post by jonboy99 on 2009-06-09
There is already a beta driver which should work - 185.something from nvidias site. The windows driver of the same version number works fine. As usual however I am not able to install it successfully on linux so will have to wait until it is installable via envy.  At least with a working nv driver I have full screen resolution now.

---

