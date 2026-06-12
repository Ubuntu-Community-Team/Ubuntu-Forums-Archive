---
title: "Joystick Mess (keeps skipping, like it's in turbo mode)"
date: 2007-07-28
forum: Gaming &amp; Leisure
---

### Post by Darth_Sirius on 2007-07-28
I was using Kubuntu 7.04 and I don't remember this problem occurring to me. The thing is that my Twin USB Joystick adapter for psx controlers is not working properly. It works in Windows though (to my disgust).

Here is the problem: it skips, like it's in turbo mode. I've installed joystick calibrator and nothing changed. I've even recompiled usb-hid module applying a patch that would solve a similar problem, but nothing changed yet.

I'm really desperate here.

I love Ubuntu, but I love gaming too.

Thank you in advance.

---

### Post by strfryed on 2007-07-30
I'm seeing the same problem on 2.6.20-16-generic.  I didn't have this problem with Debian kernels or with vanilla kernels.  I also don't have the problem on my desktop which has the same kernel.

If I have time I may try some older kernels and see if I can isolate the problem.

This is a real pain.   Can you confirm which psx adapter you are using?  I have a dualshooter II.

---

### Post by buttons on 2007-07-30
Known bug with twin adapters, kernels 2.6.18-2.6.21.  Try kernel 2.6.22 and see if that resolves the problem.  A quick and dirty way to do this is to add the gutsy repos, upgrade only the kernel, and then change everything back to feisty.

An alternative would be to downgrade to the edgy kernel, which is 2.6.17.

Or compile it yourself :)

---

### Post by acoustibop on 2007-08-01
If by 'joystick calibrator' you mean jscalibrator, I'd get shot of it, Darth_Sirius.  It seems to have a talent for deactivating controllers - several other people have found the same thing.  If you need a calibrator, try joystick.

---

### Post by luridsorcerer on 2007-08-16
I use Kubuntu, so I use KDE's joystick calibrator to calibrate.  

My Dualshock 2 to USB adapter gave me the same trouble with the insane rapid-fire.  I built myself a new kernel, 2.6.22.1, and now my controllers work perfectly.

---

### Post by SZF2001 on 2007-09-26
Just a quick plug - to upgrade to the new kernel, here's a neat guide:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

