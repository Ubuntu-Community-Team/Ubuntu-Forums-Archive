---
title: "8600M GT issues"
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by waspinator on 2008-04-26
Hi,

I'm running 8.04 on a inspiron 1520 with a 8600M GT, and after installing the nVidia 'new' driver, I get poor compiz performance, and pink/red shadows around my windows. These issues go away when I run a XGL session, but XGL has a lot of other issues that make it a poor second choice. Is there a newer driver that fixes these issues with AIXGL?

Thanks,

Waspinator

---

### Post by tempest on 2008-04-26
I am using 8.04 on a Vostro 1500 with a 8600M GT. I am having no trouble with compiz aside from a small lag from time to time due to the Nvidia PowerMizer support. I have not had any problems since I installed the 8.04 beta. I am using the version 169.12+2.6.24.12-16.34 of the nvidia-glx-new package. If I recall correctly, I used the 'Add/Remove Applications' menu to install the Nvidia 'new' driver. It is my understanding that the Vostro 1500 and the Inspiron 1520 are nearly identical.

---

### Post by waspinator on 2008-04-26
Thats weird. I wonder if there is some small detail thats different thats causing my problems. It's a fresh install, and checking the hardware drivers box doesn't work. It doesn't download. I have to manually use add/remove and install the driver, and then check the box. 

I'm using the same version of drivers as you are. I'm using the 32bit version of Ubunutu, but I don't think that would make a difference. BTW how is 64 bit? do all the applications run? (flash) I thought 64bit wouldn't be user end ready for at least another 10 years. I hope (for my sake) that other 1520 users have this issue, and that it will be addressed soon.

Thanks,

Waspinator

---

### Post by ArchLinuxFan on 2008-04-28
Theres a new fix to the pink glow bug at [http://ubuntuforums.org/showthread.php?t=772408](http://ubuntuforums.org/showthread.php?t=772408)

---

### Post by waspinator on 2008-04-29
Thanks for the tip. My 8600M still has smoother animations with XGL, but I can live with some stuttering for now. Hopefully Ubuntu will fix AIGXL (or nVidia drivers) with updates soon.

---

### Post by StefAndrew on 2008-04-30
That link helped me out too.  I goofed up and I think I had a typo the first time I did it and restarted X, it tried to go into low graphics mode.  So I went to recovery mode and re-did the link and it works perfectly now.

---

### Post by linusr on 2009-05-25
seems the nvidia driver issues are here to continue.

I use Vostro 1500 with nvidia 8600 GT 256mb and had never seen it run smooth than the vista installation.

But, one thing I noticed in 9.04 release - 64-bit runs relatively faster 32-bit. Compiz still lags and overall ubuntu still feels sluggish :(

---

