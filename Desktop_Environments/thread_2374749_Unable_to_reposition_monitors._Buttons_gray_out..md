---
title: "Unable to reposition monitors. Buttons gray out."
date: 2017-10-18
forum: Desktop Environments
---

### Post by rick-blacker on 2017-10-18
Running an Asus nVidia GTX 1080 graphics card.

I just did a complete refresh install of Ubuntu.
Both monitors work, however they are backwards. I want swap them left to right.  I bring up Settings -> Displays.  Both monitors show up. I am able to drag the monitor icons around in Display settings.  I click apply.  
The "Does this display look Ok" dialog box comes up.
I click "Keep this configuration" button

At that point, the dialog box grays out, the timer continues to count down to 0.
I am able to use my mouse.
The mouse pointer will move from one monitor to the other from left to right correctly, but not able to interact with anything on either screen.
The timer on the dialog box will finally get to 0, at which point, the "Does the display look ok" dialog box will close, and my monitors go back to being backwards.  Backwards as in, I have to move my mouse the wrong way to bet to the other monitor.

Anyone have this issue?  How do I move past it?  
Thanks!
Rick

---

### Post by Bucky Ball on 2017-10-18
Try arandr. It's in the repositories. Move the screens around, click the arrow to confirm and see if the change sticks.

---

### Post by Autodave on 2017-10-19
Did you install any drivers for the Nvidia card? If so, what one and where did you get it from?

---

### Post by rick-blacker on 2017-10-19
I did not try to install any extra drivers.
To make a long story short as possible.... 

Originally I had a different cpu/mobo/graphics card.
Installed Ubuntu onto a secondary drive, everything was fine.
Don't do anything with Ubuntu for a long time, get a new cpu/mobo/graphics card. Go about my Windows world and what not.
Recently decide I need to do some linux work, booted up into Ubuntu, only one monitor works.

Did a fresh install of Ubuntu, both monitors work now, but unable to swap monitors around.

My Graphics card is an ASUS NVida GTX 1080, which again, i have not tried to download any drivers for it.

---

### Post by Bucky Ball on 2017-10-19
Open 'Software and Updates' and in 'Other Software' enable the 'Canonical Partners' repository if it is not already enabled. Update the OS then look in 'Additional Drivers'. There will be a driver there for the NVidia card. Install and reboot.

This will give you an NVidia config tool which should let you put the screens where you like.

---

