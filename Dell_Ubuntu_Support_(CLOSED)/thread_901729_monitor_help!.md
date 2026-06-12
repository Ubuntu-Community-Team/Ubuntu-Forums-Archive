---
title: "monitor help!"
date: 2008-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sanjuuichisandoichi on 2008-08-26
So I just bought an s-video cable hoping to be able to use my computer as a makeshift dvd player.

when I tried to add the monitor i think i just hit system, administration, screens and graphics, model, and pressed detect.  This moved me to plug and play and I pressed okay.  This then required me to logout to see any changes.  When I logged back in I couldn't see anything on the tv nor could I restore my laptop screen back to its original resolution.  I don't know what I need to do in order to accomplish either of these things but I would like to do both.

I'm running 7.10 on a 1420n with the nvidia graphics card.
Please help, this 640 x 480 resolution is driving me crazy!

---

### Post by Diggs808 on 2008-08-27
> **sanjuuichisandoichi said:**
> So I just bought an s-video cable hoping to be able to use my computer as a makeshift dvd player.

when I tried to add the monitor i think i just hit system, administration, screens and graphics, model, and pressed detect.  This moved me to plug and play and I pressed okay.  This then required me to logout to see any changes.  When I logged back in I couldn't see anything on the tv nor could I restore my laptop screen back to its original resolution.  I don't know what I need to do in order to accomplish either of these things but I would like to do both.

I'm running 7.10 on a 1420n with the nvidia graphics card.
Please help, this 640 x 480 resolution is driving me crazy!


Go to synaptic and install the nvidia-settings package.  This is a gui, made by nvidia, for your graphics card.  

It is a gui program so it can be launched (once installed) from **System > Administration > NVIDIA X Server Settings** 

once the app launches click on **X Server Display Configuration**

It should show both displays. The monitor should be identified as disabled. (If not click on Detect Displays). Click on the monitor then click on the button that says configure. Click on Twinview. That activates the monitor on the program. Change the resolution to the one that you want. Click on Apply. 

If you want to you can also click on "Save to X Configuration File"

Hope that this helps

---

