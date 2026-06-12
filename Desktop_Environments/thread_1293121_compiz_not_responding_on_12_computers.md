---
title: "compiz not responding on 1/2 computers"
date: 2009-10-16
forum: Desktop Environments
---

### Post by yanvolking on 2009-10-16
Hello Community,

I have installed compiz on my laptop computer and it works fine: I gott the rotating cube effect by clicking on the boxes in the configuration menu.
my laptop's video card is :
 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Now, when I install compiz on my desktop computer (a much more recent machine) I click the right boxes on the configuration menu but nothing happens.  It's as though compiz had not been installed at all with the only exception that the configuration menu is there.  The video card on my desktop is:
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)

Both computers have undergone exactly the same ubuntu / windows XP dual boot installation process.  Could it be that the video card of my desktop requires a driver not supported by UBUNTU or something like that?.

What do I have to do to get compiz to work on my desktop?

Thanks

Y.

---

### Post by wojox on 2009-10-16
Did you install the nvidia driver?

How about System > Preferences >  Enable Desktop Effects

---

### Post by yanvolking on 2009-10-16
JUST ONE MORE THING: when I run the hardware check on my desktop I get the resulting message :

NVIDIA accelerated graphics driver (version 180) (recommended)  This driver is not activated
3D-accelerated proprietary graphics driver for NVIDIA cards.
This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.
If you wish to enable desktop effects, this driver is required.
If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games.

When I activated it, my screen instantly went scrambled.  I took me an incredible effort to find my way back to the disactivate button through all that scrambled image to get back to the old setting.  

My screen is an old (1994) Cathode Ray model with max 800 x 600 resolution and 60Hz refresh rate.  Is this screen incompatible with the Nvidia driver?  

Is the Nvidia driver the key to get compiz to work?  Can it be done with my old screen?



Thanks

Y.

---

### Post by baffledsimian on 2009-10-16
If you activated the recommended driver and it scrambled the display on your victorian era CRT, then it might be time to invest in a flat screen. I'm not sure that the CRT cannot handle the latest nvidia video signals, but I would think that if you choose a recommended driver in Ubuntu, it should in theory work properly. The first thing to do when compiz doesn't work is to ensure you have the latest nvidia drivers. Since you seem to have done that, I would recommend you go to The Antiques Roadshow, seeing how much you can get for the CRT and then buying a flat screen with the proceeds.

---

