---
title: "Why is Ubuntu being so buggy?"
date: 2010-08-29
forum: Desktop Environments
---

### Post by Refresh100 on 2010-08-29
My Ubuntu (10.04 LTS) has been _really_ buggy lately. For example, it's has been really slow, the sound driver (ALSA) wasn't working right (until I updated it) and every now and again my panels act up and I can't get to certain parts without using Panel Restore. I don't get it, it used to be fast and responsive, that why I started using it more than Windows (still a dual-booter). Please help me.

---

### Post by meditatingfrog on 2010-08-29
> **Refresh100 said:**
> My Ubuntu (10.04 LTS) has been _really_ buggy lately. For example, it's has been really slow, the sound driver (ALSA) wasn't working right (until I updated it) and every now and again my panels act up and I can't get to certain parts without using Panel Restore. I don't get it, it used to be fast and responsive, that why I started using it more than Windows (still a dual-booter). Please help me.

Hey Refresh100:

Here's what I'm thinking.  You might want to see if it's particular packages that have bugs, or if it's the kernel.  Have you tried using a different kernel, to see if the problems still persist?  Grub should give you an option to try older kernels than the one you are booting with.  If ubuntu used to work for you in the past, it is probably the newer kernel that is causing the problems.

---

### Post by David Andersson on 2010-08-29
Some ideas to try to locate the problem:

1) If one login with session=failsafe by mistake, one can encounter unexpected problems. In 10.04, session is reset automatically, but just in case, check that session is not "failsafe" when you login.

2) Sometimes, especially after upgrades, old user preference settings can cause problems. To test if that is the case one can create a new dummy user, login as that user, and see if she is experiencing the same problems.

To create a new user, go to System > Administration > Users and Groups. Create a new user named "dummy" or "alterego" or whatever. Then logout and login as that user. If it has the same problem, it is a problem with the system, and not with the user settings.

---

