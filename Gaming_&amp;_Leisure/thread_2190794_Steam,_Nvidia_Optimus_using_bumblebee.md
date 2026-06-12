---
title: "Steam, Nvidia Optimus using bumblebee"
date: 2013-11-29
forum: Gaming &amp; Leisure
---

### Post by Kaijday on 2013-11-29
Is there a decent guide to getting Nvidia optimus cards working under steam for 64bit?

I have an Intel HD4000, with a NVIDIA GT635M. If I try to run steam, it says a 32bit lib is missing. But as I am using Bumblebee, I am unsure on how to go about getting this to work? I don't want my NVIDIA card on all the time, it drains my very good laptop battery.

Many thanks,
Kai

---

### Post by efflandt on 2013-11-29
I just went through that after installing 64-bit 13.10 on a new gaming laptop, so that may help you [http://ubuntuforums.org/showthread.php?t=2188201](http://ubuntuforums.org/showthread.php?t=2188201)

I got **steam** working with the Intel video and additional parameters needed to launch TF2 or other source games using **optirun** (bumblebee) for nvidia graphics. I have not tried other steam games on it yet.

---

### Post by Kaijday on 2013-11-29
Cheers, I'll take a look at that.

---

### Post by Kaijday on 2013-11-30
> **efflandt said:**
> I just went through that after installing 64-bit 13.10 on a new gaming laptop, so that may help you [http://ubuntuforums.org/showthread.php?t=2188201](http://ubuntuforums.org/showthread.php?t=2188201)

I got **steam** working with the Intel video and additional parameters needed to launch TF2 or other source games using **optirun** (bumblebee) for nvidia graphics. I have not tried other steam games on it yet.

Worked a treat, cheers. Just a question, do you have any drivers installed for your discrete card? I don't, and performance seems okay. But would having drivers for it improve it more?

---

### Post by lucidlytwisted on 2013-12-01
> **Kaijday said:**
> Worked a treat, cheers. Just a question, do you have any drivers installed for your discrete card? I don't, and performance seems okay. But would having drivers for it improve it more?

If you don't have drivers installed (either proprietary or open) for the nvidia card, then it's probably falling back to using the integrated graphics. Although I'm surprised you didn't get an exception.

---

### Post by efflandt on 2013-12-02
I installed nvidia-experimental-310, which is actually 319.60 drivers in Ubuntu 13.10. Steam recommended experimental drivers back when I first installed it on my desktop during beta in January (in Ubuntu 12.04 nvidia-experimental-310 is currently 319.32). That works fine for steam and games on both computers.

If you did not install any **nvidia** drivers you would be using the default **nouveau** driver. I did not try optirun (bumblebee) before installing nvidia drivers, but that is likely not as fast.

---

### Post by Kaijday on 2013-12-03
I have no drivers listed under the hardware thing, so I'll try the experimental. Thanks

---

