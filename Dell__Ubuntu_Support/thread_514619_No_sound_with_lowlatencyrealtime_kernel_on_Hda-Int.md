---
title: "No sound with lowlatency/realtime kernel on Hda-Intel (SigmaTel STAC9228) audio card"
date: 2007-07-31
forum: Dell  Ubuntu Support
---

### Post by flowbot on 2007-07-31
Audio on my Inspiron 1420 only works with the generic kernel (albeit, so long as this fix is applied). However, I want to indulge in some realtime/lowlatency audio production (too many xruns with generic kernel), so installed both kernels from synaptic. While the hda-intel card seems to be detected, it doesn't output any sound in the lowlatency or realtime kernels.

Can anyone else with this audio card test out the lowlatency or realtime kernels and tell me if they can get sound?

---

### Post by AnalogIC on 2007-12-24
I have the same exact problem. I don't know what to do, 'cause I was trying to install de rt-kernel, to work with ardour. I have ubuntu 7.04 specially customized  by dell (for the 1420 model.)

If you find any solutions please let me know.

I configure jack to minimize the xruns with the generic kernel. But the results are not quite efective for real tiem proccesing

I'm really frustrated, because this is the only issue that keeps me using Win$. :( 

thanks in advance.

---

### Post by fragos on 2007-12-24
Dell now has a download for a Dell 7.10 DVD.  Works like a charm on my 1420n.  7.10 would be my next step.

---

### Post by AnalogIC on 2007-12-30
I have downloaded that ISO too. Check dell's site for known bugs.
If you have any experience testing the rt-kernel, please tell me if you got any results.

Happy new year!!!

---

### Post by AnalogIC on 2008-01-08
I installed dell's ubuntu  7.10. (I burned  the iso avaliable from dell linux site)
Installed ubuntustudio packages via synaptic.
after reboot, in GRUB now I have the option to start with realtime kernel.
when I start with kernel-rt, no sound avaliable.
but when I start with generic kernel sound works fine.

the problem: I need to work with the realtime kernel,  customized to work with realtime audio aplications. but audio on that kernel is not avaliable.

Please help!

thanks in advance.

---

### Post by fragos on 2008-01-08
Right click the volume icon in the upper applet bar and select Preferences.  The first choice is for the device.  Mine says "VIA 8237 (Alsa mixer)" which works.  I have two other choices which don't.  One of them is for my TV tuner card.  I'd look here next because this control says which device gets access to sound.

---

### Post by SamFrew on 2008-05-25
I had similar problems until I used Method G (I'm using a Dell D630) from:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

I replaced "generic" with "rt" (for the realtime kernel) in the given command, i.e.

sudo aptitude install linux-backports-modules-rt

Now I have sound in both my generic and rt kernels.

---

