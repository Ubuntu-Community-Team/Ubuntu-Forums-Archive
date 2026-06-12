---
title: "Older ATI RADEON card"
date: 2005-07-27
forum: Gaming &amp; Leisure
---

### Post by BionicBigfoot on 2005-07-27
I wont pretend that I know much about linux. I downloaded and installed Ubunto H.H. for a machine I had sitting around with an older ati radeon 7500. I would like to know if there are any EASY (I am so much of a newbie here) set of instructions to get the drivers installed and working? How do I know if Ubunto actually installed the correct OpenGl driver to begin with. 

I downloaded H.H. Today and I don't even know where to find the Kernel information for my download.

I want to migrate to Linux as I think Microsoft really does some bad business practices. I am actually excellent in mucking up Windows and messing around with it but the language at linux is almost foreign to me.

Anybody wanna help me get my old card to work with some old games like Unreal Tournament...I know I have to install Wine and the step by step for that seems pretty easy. I just wont install it until I know I have ati drivers working. 

Oh and the instructions on the DRI Project web page are for more experienced users. I am a real newbie!

---

### Post by albertomm on 2005-07-28
> Oh and the instructions on the DRI Project web page are for more experienced users. I am a real newbie!

Do you have 3D acceleration? To find out, type:
glxinfo | grep 'direct rendering'

If it says "yes", you're done!

If it says "no", do this:

First, "sudo dpkg-reconfigure xserver-xorg". When the wizard asks you for the driver to use, select "radeon". The other questions should be already well configured so don't touch it.

Try again the glxinfo command. If it says no, then you have to load the appropiate modules for the AGP port. Usually they are "ati-agp" and the one for your motherboard (in my case, i have an asus with via chipset, so is "via-agp").

I hope it helps.

---

