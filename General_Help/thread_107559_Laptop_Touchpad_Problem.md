---
title: "Laptop Touchpad Problem"
date: 2005-12-23
forum: General Help
---

### Post by martianpenguin on 2005-12-23
I recently installed ubuntu on my laptop.  It was working fine, until I needed a specific ethernet over USB driver.  The driver does not work in kernel versions 2.6.12 and 2.6.13, so I had to upgrade to 2.6.15.  When I upgraded the kernel, the touchpad no longer worked correctly.  When I touch the touch pad, it appears to be similar to holding down the middle button of the mouse, and it does not move the mouse at all.  As of right now, I use a USB mouse and disable the touchpad by modprobe -r psmouse.  This is alright for now, but I will need to be able to use the laptop without an external mouse in the future, so I'd like to get this fixed.  

If you need more info to help me, just ask.

If this should be in a different forum, I'll repost there.

-martianpenguin

---

### Post by BathroomNinja on 2005-12-23
More than likely, it is a module that was enabled by default on the older kernels and not on the newer one.  What is the model of your laptop?  Also, did you compile the kernel yourself?

---

### Post by martianpenguin on 2005-12-23
I have an Alienware Sentia.

I tried the kernel for dapper and compiled my own from sources, both give the same problem.

When I disable psmouse by using modprobe, it stops responding at all.  Wouldn't that mean that psmouse is the module that is controlling the touchpad?

---

### Post by BathroomNinja on 2005-12-23
yeah, sounds like it.  You might want to file a bug.  I'll look around to see if I can find any patches.

EDIT- which release canidate are you using?

---

### Post by martianpenguin on 2005-12-23
is it possible to install a module from an old kernel?  It was working fine on the 2.6.12 kernel.

---

### Post by BathroomNinja on 2005-12-23
I honeslty have no idea :( 
Perhaps message one of the guys who wrote the 'kernel compile' howto's?

---

