---
title: "Desktop zoom not working on Ubuntu 7.10"
date: 2008-04-11
forum: Desktop Effects &amp; Customization
---

### Post by rsf33 on 2008-04-11
I installed Ubuntu 7.10 on my desktop PC and the Desktop Zoom feature worked perfectly out of the box. When I hold the Super key and turn the mouse wheel, I can zoom in and out. This is very helpful as I have low vision.

Next I installed Ubuntu 7.10 on my laptop (an old Sony Vaio) and I cannot get the Desktop Zoom to work. I really need the Zoom to work on the laptop because of my visual impairment. Unfortunately, nothing happens when I hold the Super key on the laptop and turn the mouse wheel.

The laptop is a Sony Vaio PCG FX390 and has the Intel 82815 graphics card. If I go to the System->Administration->Screens and Graphics menu, I see that the graphics card is correctly identified as the Intel 82815. The driver is shown as "Intel experimental modesetting driver".

Does anybody know if Desktop Zoom is simply not compatible with the graphics card or driver? Or does anybody have any suggestions on how to troubleshoot this problem?

Thank you for your help!

- Roger

---

### Post by tommyhakinen on 2008-04-13
Did you have CCSM installed? It has zoom desktop features too. You can try it. You can install it with this :

> sudo apt-get install compizconfig-settings-manager

hope this will help.

---

### Post by rsf33 on 2008-04-13
Thank you for the tip about CCSM. I did not have it installed, and so I installed it with the command you provided. I then used CCSM to verify that "Enhanced Zoom" was enabled, but neither regular zoom nor enhanced zoom would work.

I found a posting on the web that mentioned in passing that hardware 3D acceleration was required in order to use zoom. I checked the man page for my Intel video driver and found that it does not support hardware 3D acceleration in 24 bit color depth mode.

So I edited my xorg.conf file to switch to 16 bit color depth, and now I was able to enable visual effects from System->Preferences->Appearance->Visual Effects. 

Now both zoom and enhanced zoom work. Unfortunately, the display has lots of rendering problems now that visual effects are enabled. (Wrong things are displayed around the mouse pointer sporadically when I move the mouse.)

Thank you for your help. At least this is moving in the right direction!

- Roger

---

