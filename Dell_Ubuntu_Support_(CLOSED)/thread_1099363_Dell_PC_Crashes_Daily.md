---
title: "Dell PC Crashes Daily"
date: 2009-03-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thexder31 on 2009-03-18
With the latest Ubuntu, my old Dell 370 Seems to crash frequently.  It usually does this when interacting with the UI.  Meaning, I'm manipulating the UI and the whole PC locks up (everything is down, telnet fails, keyboard non-responsive (e.g. caps lock light non responsive).  Only way to reboot is hard-kill (press/hold power button).

Most recently, I seem to be able to associate the crash with pressing alt-tab.  

The PC is slightly non-standard.  I have two belkin USB cards installed in the back, with nothing plugged in (perhaps the keyboards... unclear).  

In general,  I've never had a Linux PC lock up on me; this is pretty shocking.  Any thoughts?

---

### Post by armandh on 2009-03-18
you are already suspcious of hardware
do the usual substitution to test
Don't forget to try a different keyboard.

you should see what a bad mouse cord will do!!!!

---

### Post by ugm6hr on 2009-03-18
Hardware specs?

RAM /  free HD space?

---

### Post by jespdj on 2009-03-18
When you boot your computer, select "memtest86+" from the GRUB boot menu (you may have to press Esc while booting to see the menu) to run the memory test program.

Let it run for a few hours to thoroughly test yout memory. If it finds any errors, then it is very likely that the memory in your computer does not work properly anymore.

The cause of random crashes is most often a hardware problem.

---

### Post by khelben1979 on 2009-03-18
> **thexder31 said:**
> With the latest Ubuntu, my old Dell 370 Seems to crash frequently.

Maybe the kernel which is shipped with Ubuntu Intrepid doesn't like your hardware?

One other thing it could be is that the heat inside have damaged something. Powersupplies is a vital part for instance.

---

### Post by thexder31 on 2009-03-18
Thanks all... Predominantly you guys seem to think the likely cause is hardware rather than USB card/kernel incompatibilities.  The only thing that concerns me with this thought is that the hardware was stable for 3+ years running windows XP (of all things) without the cards, and for 1+ year with the cards.  Anyways, I think the hardware statements are valid.  Probably I'll try the memtest as well removing the belkin cards. And if I really get desperate, I'll swap out other peripherals. Thanks!

---

### Post by pal8 on 2009-03-24
I've had the same problem. A Dell D420 with Ubuntu 8.10, that used to run XP without a problem.

---

### Post by sirebral on 2009-03-24
You might consider installing the Linux Backports.  It might not be a hardware problem but a problem understanding the hardware (ie. drivers).  Something with the hardware though.

---

### Post by pal8 on 2009-03-24
> **sirebral said:**
> You might consider installing the Linux Backports.  It might not be a hardware problem but a problem understanding the hardware (ie. drivers).  Something with the hardware though.

Not sure what it is. I found backports.org, is that it? It didn't explain too well.

---

### Post by dgray_from_dc on 2009-03-24
> **pal8 said:**
> Not sure what it is. I found backports.org, is that it? It didn't explain too well.

I think backport means older (sometimes considered outdated) software (or in your case drivers) made to work with new or current software.  Think of a reliable Win98 driver made to work with XP.  I'm not sure if that's exactly it, but I think that's the general meaning.  You can enable the backports repository in you package manager.

---

### Post by sirebral on 2009-03-25
> **dgray_from_dc said:**
> I think backport means older (sometimes considered outdated) software (or in your case drivers) made to work with new or current software.  Think of a reliable Win98 driver made to work with XP.  I'm not sure if that's exactly it, but I think that's the general meaning.  You can enable the backports repository in you package manager.

Sounds about right.  And yes, you can enable them in the package manager.  The reason I suggest it is because your computer looks a little dated.

---

### Post by ugm6hr on 2009-03-25
> **dgray_from_dc said:**
> I think backport means older (sometimes considered outdated) software (or in your case drivers) made to work with new or current software.  Think of a reliable Win98 driver made to work with XP.  I'm not sure if that's exactly it, but I think that's the general meaning.  You can enable the backports repository in you package manager.

The backports repository is where *newer* versions of software for a *newer* version of Ubuntu are modified to work with an *older* version of Ubuntu.

From a drivers viewpoint, it is most useful for newer previously unsupported hardware.

---

