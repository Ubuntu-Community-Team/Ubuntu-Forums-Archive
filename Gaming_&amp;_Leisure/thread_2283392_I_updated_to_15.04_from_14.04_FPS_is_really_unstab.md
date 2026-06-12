---
title: "I updated to 15.04 from 14.04 FPS is really unstable."
date: 2015-06-21
forum: Gaming &amp; Leisure
---

### Post by cooleryawner on 2015-06-21
On Ubuntu 14.04, I avg. around 100 fps, on 15.04, it keeps jumping between 9 and 100. The game is Counter-Strike Global Offensive.

---

### Post by MikeCyber on 2015-06-22
Usually after a update, you need to manually update/reinstall your graphics driver. For Nvidia I only download the latest from Nvidia, as all is in place, making install a piece of cake.

---

### Post by Bucky Ball on 2015-06-22
Off-topic, but I'm always curious as to why users upgrade from a working, five year support LTS install to an interim support that is supported for nine months. Was there a major reason? 14.04 LTS lacked a specific driver? You were having issues? 

To your issue, was it a clean install or did you jump through the 14.04> 14.10> 15.04 net upgrade hoops?

---

### Post by cooleryawner on 2015-06-22
> **Bucky Ball said:**
> Off-topic, but I'm always curious as to why users upgrade from a working, five year support LTS install to an interim support that is supported for nine months. Was there a major reason? 14.04 LTS lacked a specific driver? You were having issues? 

To your issue, was it a clean install or did you jump through the 14.04> 14.10> 15.04 net upgrade hoops?

I jumped through the upgrade hoops.

P.S. I upgraded because I thought, "why not? I just added a bunch of space to my Ubuntu partition." Also, I thought that would fix the major lag I was having when I try to use Budgie desktop, bad idea, Budgie doesn't even support 15.04.

---

### Post by cooleryawner on 2015-06-22
> **MikeCyber said:**
> Usually after a update, you need to manually update/reinstall your graphics driver. For Nvidia I only download the latest from Nvidia, as all is in place, making install a piece of cake.

I usually use the non-proprietary drivers, but I am willing to give the ones made by the GPU company(AMD in my case) a try, do you know any good tutorials?

---

### Post by MikeCyber on 2015-06-23
I use Nvidia but probably:
open the system preferences and look for "Additional Drivers"
or in synaptic.
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by Bucky Ball on 2015-06-23
> **cooleryawner said:**
> 

P.S. I upgraded because I thought, "why not? I just added a bunch of space to my Ubuntu partition." Also, I thought that would fix the major lag I was having when I try to use Budgie desktop, bad idea, Budgie doesn't even support 15.04.

For future reference, be aware that upgrading an unstable or broken system via the net has a 99% chance of not fixing anything. :)

As suggested by MikeCyber, try Additional Drivers (after an update) and see if you have a driver waiting to go. Good luck with your current issue.

---

### Post by cooleryawner on 2015-06-23
> **Bucky Ball said:**
> For future reference, be aware that upgrading an unstable or broken system via the net has a 99% chance of not fixing anything. :)

As suggested by MikeCyber, try Additional Drivers (after an update) and see if you have a driver waiting to go. Good luck with your current issue.

Do you think I should use the Ubuntu driver or the Linux driver, the Ubuntu problem is it is built for 14.04, but it was released the same day as the linux driver, both were released on the 2nd of this month.

---

### Post by cooleryawner on 2015-06-23
I have tried installing the linux driver, and now i get this error
```
 aticonfig: No supported adapters detected


```

---

### Post by QIII on 2015-06-23
Hello!

I may have missed it, but what is the model of your graphics adapter?

---

### Post by cooleryawner on 2015-06-23
> **QIII said:**
> Hello!

I may have missed it, but what is the model of your graphics adapter?

I have an AMD Radeon HD 7730M.

---

### Post by QIII on 2015-06-24
"M" indicates a mobile device or a laptop.  Is this a hybrid graphics machine?

---

### Post by cooleryawner on 2015-06-24
> **QIII said:**
> "M" indicates a mobile device or a laptop.  Is this a hybrid graphics machine?

yes, and I followed the instructions for the hybrid graphics driver installation from the [https://help.ubuntu.com/community/BinaryDriverHowto/AMD#Manually_installing_Catalyst_13.4.2C_special_case_for_Intel.2FAMD_hybrid_graphics](https://help.ubuntu.com/community/BinaryDriverHowto/AMD#Manually_installing_Catalyst_13.4.2C_special_case_for_Intel.2FAMD_hybrid_graphics) page.

---

### Post by michael-piziak on 2015-06-24
> **Bucky Ball said:**
> Off-topic, but I'm always curious as to why users upgrade from a working, five year support LTS install to an interim support that is supported for nine months

Me too.  I'm still using 12.04 LTS which is supported until April of 2017.  Fewer of my game emulators worked under 14.04 lts, so I went back to 12.04 LTS.   Everything works smoothly so why upgrade ?

---

### Post by cooleryawner on 2015-06-28
So I decided to just install Linux Mint and delete Ubuntu. Perfect, the drivers work perfectly and the game runs smooth. This is now solved.

---

### Post by MikeCyber on 2015-06-29
@cooleryawner what's different?

@michal-pizak I have no problems with 15.04 at all.

---

