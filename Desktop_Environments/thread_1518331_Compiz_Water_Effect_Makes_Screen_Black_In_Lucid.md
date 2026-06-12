---
title: "Compiz Water Effect Makes Screen Black In Lucid?"
date: 2010-06-26
forum: Desktop Environments
---

### Post by w0Rm210 on 2010-06-26
Hey guys im using Ubuntu 10.04 and i just need help getting the water effect working correctly whenever i enable it and try to iniate it it just makes my screen black =/. It sucks because i really loved that feature (on 64-bit btw) well any help is appriciated :).

---

### Post by w0Rm210 on 2010-06-27
Does anyone know? Maybe a compiz pro? I really did love that feature :(

---

### Post by Yarui on 2010-06-27
This is just a shot in the dark, but it could be because the video driver you are using doesn't have 3d acceleration fully functional for your current setup.  If it isn't explicitly a 3d acceleration issue I would be willing to bet that it is a driver issue one way or another.  Try searching for some threads where people are discussing drivers for your specific card, or give your system specs here and someone may be able offer some advice.

---

### Post by w0Rm210 on 2010-06-27
> **Yarui said:**
> This is just a shot in the dark, but it could be because the video driver you are using doesn't have 3d acceleration fully functional for your current setup.  If it isn't explicitly a 3d acceleration issue I would be willing to bet that it is a driver issue one way or another.  Try searching for some threads where people are discussing drivers for your specific card, or give your system specs here and someone may be able offer some advice.

Yeah well a friend of mine is having the exact same prob. Like to the T but ill post my specs anyway.
---------------------------------------------------------------

My graphics card is an ATI M880G Radeon HD 4200
Subsystem : : HP Device 363F
---------------------------------------------------------------
My CPU is a AMD Sempron(tm) M120 800.000 MHz
L2 Cache=512 KB
===================================
I hope someone can help =/

---

### Post by Yarui on 2010-06-27
If you have a Radeon HD 4200 I think that may be your problem.  I have the same onboard video card and had some trouble getting 3d acceleration to work on it.  While I was trying to get decent drivers installed I found some documentation that said that the Radeon drivers don't have full support for the HD 4200.  I just checked and I get the same issue with the compiz rain effect.  You may have to wait a while for support to be added for your card, or if that doesn't end up happening you might have to live without that feature until you upgrade your hardware.

---

### Post by w0Rm210 on 2010-06-27
Alright thank you the effect should work on the netbook im building so ill have it either way lol. Thanks for your answer :)

---

### Post by Yarui on 2010-06-28
No problem.  If you ever end up finding some way to fix it, post your solution here.  I'll try to remember to do the same thing.

---

### Post by PGHammer on 2010-06-28
> **Yarui said:**
> If you have a Radeon HD 4200 I think that may be your problem.  I have the same onboard video card and had some trouble getting 3d acceleration to work on it.  While I was trying to get decent drivers installed I found some documentation that said that the Radeon drivers don't have full support for the HD 4200.  I just checked and I get the same issue with the compiz rain effect.  You may have to wait a while for support to be added for your card, or if that doesn't end up happening you might have to live without that feature until you upgrade your hardware.

However, the proprietary AMD drivers *do* support the HD series (from HD2xxx up) including the Mobility models; they support models in that range that the base FOSS drivers don't (such as the HD5xxx series).  Consider using those (System-> Hardware Drivers).  I had to use those for my HD5450 as the HD5xxx cards have no 3D support without them (though 2D is supported using the FOSS drivers, depending on distribution, performance is much improved even there with the proprietary drivers).

---

### Post by w0Rm210 on 2010-06-28
Yeah thats what i did was enable the 3D acceleration but it still dosent work and it dosent seem to be working on 10.10 alpha 1 either. Kinda weird but yeah actually without that driver the basic extra effects dont even work with ati. =/

---

### Post by bluff on 2011-01-28
I have the rain effect working now on my ATI Mobility Radeon HD 5600/5700 Series.

The only way I got it working was by uninstalling the driver reccommended by ubuntu installer. Then installing it manually from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx). now all is fine. Seems that the driver that ubuntu installs doesn't really enable all 3D options, I am using Ubuntu 10.04 if this helps.

---

### Post by neverama on 2012-08-27
Check GTK loader plugin is OFF. Had this issue even on Ubuntu 12.04 Precise.

Also try with different combinations of the Blur Plugin (switching gaussian, mipmap or bilinear with low numbers and flash screen enabled in the water plugin to begin testing it with), have solved it for me on different hardware. (ATI/Nvidia).

---

### Post by overdrank on 2012-08-28
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

