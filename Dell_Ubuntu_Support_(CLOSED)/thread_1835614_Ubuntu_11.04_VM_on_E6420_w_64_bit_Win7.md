---
title: "Ubuntu 11.04 VM on E6420 w/ 64 bit Win7"
date: 2011-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TuskBilly on 2011-08-29
I have a Dell E6420 w/ quad core I7, 4GB & NVidia NVS 4200M graphics.  Base OS is 64 bit Win 7.  I have Ubuntu in a VM.  My issue...  The Ubuntu VM launches in an 800X 600 window.  I can't get it any larger.  When I try to launch Evolution, the config wizzard is larger than the window I'm working in so I can see it all.  I can't resize the window and I can't scroll.  I'm guessing I didn't do something correct when I built the VM but I can't figure out how to make the window bigger at this point.  When I "maximize" the VM window it just shifts to the top left corner of the screen at the ame size.
 
Suggestions?  If I blow it away and start over will I readily see where I messed this one up?
 
Thanks for helping.

---

### Post by rickyjones on 2011-08-30
> **TuskBilly said:**
> I have a Dell E6420 w/ quad core I7, 4GB & NVidia NVS 4200M graphics.  Base OS is 64 bit Win 7.  I have Ubuntu in a VM.  My issue...  The Ubuntu VM launches in an 800X 600 window.  I can't get it any larger.  When I try to launch Evolution, the config wizzard is larger than the window I'm working in so I can see it all.  I can't resize the window and I can't scroll.  I'm guessing I didn't do something correct when I built the VM but I can't figure out how to make the window bigger at this point.  When I "maximize" the VM window it just shifts to the top left corner of the screen at the ame size.
 
Suggestions?  If I blow it away and start over will I readily see where I messed this one up?
 
Thanks for helping.

What VM software? For VMWare or VirtualBox you will need to install the Guest Tools or Guest Additions in order to make that work properly. 

Thanks,
Richard

---

### Post by TuskBilly on 2011-08-30
Using the built in Virtual PC technology in Win 7

---

### Post by rickyjones on 2011-08-30
Might take a little work. According to Wikipedia ([http://en.wikipedia.org/wiki/Windows_Virtual_PC#Virtual_Machine_Integration_Components](http://en.wikipedia.org/wiki/Windows_Virtual_PC#Virtual_Machine_Integration_Components)) Linux is not fully supported in that product.

> Linux guests
Installing a Linux-based guest environment in Virtual PC is possible. RedHat and SuSe Linux guests are supported. Linux additions are supported in Microsoft Virtual Server, and these additions should also work in Virtual PC.[53]
Some Linux distributions must be installed in text mode, as they do not support Microsoft Virtual PC's emulated graphics chip. Ubuntu 8.10 (Intrepid Ibex) must be installed in SafeMode, but does not require other changes.
Some websites specialize in listing operating systems that run successfully as Virtual PC guests, to help users avoid issues when installing Linux distributions or other operating systems lacking official Microsoft support.

I'd recommend finding the Virtual Server addons files or, alternatively, using a different vendor. I've had great luck with VirtualBox or VMWare Workstation (not free) or VMWare Server (free).

Hope this helps!

-Richard

---

