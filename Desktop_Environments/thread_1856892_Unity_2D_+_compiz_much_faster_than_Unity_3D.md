---
title: "Unity 2D + compiz much faster than Unity 3D"
date: 2011-10-09
forum: Desktop Environments
---

### Post by superyounan1 on 2011-10-09
Hello all,
I'm running 11.10 beta in **Vbox** on a Windows host, I'm sure I'm not the only one. I'm having an annoying frame rate issue when using the default unity3d session where all the desktop environments are slow and tear on the screen, and video playback is slow as well (looks unaccelerated). One thing I noticed is that if I drag windows to the top of the screen to invoke the Aero-snap transparent overlay, suddenly frame rate is quick and slick, and as soon as I pull away from the top or let it maximizte the problem returns. 

I remember encountering this with 11.04 but was able to fix it by using ccsm to disable the "sync to vblank" option, but this isn't helping this time. I also tried playing with the auto-detect of refresh rate, and increasing the refresh rate, to no avail.

Unity 2d is another story, videos run just fine, and I can even run "compiz --replace" to get my wobbly windows and other animations, all running perfectly smooth. 

Anyone come across this in 11.10? Fixed it?

---

### Post by superyounan1 on 2011-10-09
Another interesting tidbit - while in the default unity 3d session, I did something that caused the unity plugin to crash apparently (launcher gone), desktop animations turned nice and quick. Got into CCSM and enabeled the Unity plugin, all back to being slow.

---

### Post by superyounan1 on 2011-10-09
bump

---

### Post by 3Miro on 2011-10-09
As the name suggests, Unity 3D requires 3D acceleration. Last time that I checked, Vbox supported 3D acceleration only as an experimental feature. Giving a virtual machine direct access to the GPU is apparently tricky business. As a result of that, most 3D apps don't run well under Vbox and there is nothing that can be done. Actually, I am surprised you managed to get compiz at all. Are you sure you are running Compiz + Unity 2D?

At any rate, don't look at Vbox as any sort of indication on how Unity 3D performs in real circumstances.

Unity 2D will be a bit slow (virtual machines are a bit slower in all cases), but other than that, you should get all the features in a reasonable way.

---

### Post by superyounan1 on 2011-10-10
> **3Miro said:**
> As the name suggests, Unity 3D requires 3D acceleration. Last time that I checked, Vbox supported 3D acceleration only as an experimental feature. Giving a virtual machine direct access to the GPU is apparently tricky business. As a result of that, most 3D apps don't run well under Vbox and there is nothing that can be done. Actually, I am surprised you managed to get compiz at all. Are you sure you are running Compiz + Unity 2D?

At any rate, don't look at Vbox as any sort of indication on how Unity 3D performs in real circumstances.

Unity 2D will be a bit slow (virtual machines are a bit slower in all cases), but other than that, you should get all the features in a reasonable way.

Thanks for your input.
I use Virtualbox to preview the distros, not much more. I've seen plenty of youtube screencasts grabbed from virtualbox installs that don't seem to suffer from my same problem, but I don't mind living with unity 2d for now.

Thanks anyway

---

### Post by 3Miro on 2011-10-10
> **superyounan1 said:**
> Thanks for your input.
I use Virtualbox to preview the distros, not much more. I've seen plenty of youtube screencasts grabbed from virtualbox installs that don't seem to suffer from my same problem, but I don't mind living with unity 2d for now.

Thanks anyway

You can get some 3D graphics to work under Virtual box, however, this is hardware specific and it sometimes requires special tweaking. YouTube videos try to show the best, which is not always representative of the average experience.

I used to test distros under VirtualBox, but I gave up on it as it doesn't really capture the full potential of a distro. I just got a large HDD and partitioned it so I can have five distros installed as multi-boot.

You can play with the settings yourself, you may be able to improve the performance. Look at both VirtualBox, the VB drivers as well as the specific Unity settings. Sometimes disabling just one feature, may circumvent a bug and fix all issues.

---

