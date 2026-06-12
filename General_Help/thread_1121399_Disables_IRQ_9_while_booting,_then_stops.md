---
title: "Disables IRQ 9 while booting, then stops"
date: 2009-04-10
forum: General Help
---

### Post by BlueCanary9999 on 2009-04-10
I'm new to Linux, using Ubuntu 8.10 64bit on a Lenovo Y530.  I was trying to fix my brightness according to [this post]("http://ubuntuforums.org/showthread.php?t=870681&page=21"), and when I tried to reboot, the loading bar depleted all the way, and then nothing happened (so I hard-booted).  Now when I try to boot it says something like "irq 9: nobody cared (try booting with the "irqpoll" option)".  It eventually says "Disabling IRQ 9..." for roughly 20 minutes, and then it boots.  When it turns off, the loading bar depletes and then it won't do anything for at least 30 minutes.  Pressing the power button without holding now will turn it off.

Specifically, it says:

Boot from (hd0,5)  ext3  7313cf1b-87b9-41d5-a5ae-693ef594c1bd
Starting up ...
[    3.784061] irq 9: nobody cared (try booting with the "irqpoll" option)
[    3.784237] handlers:
[    3.784307] [<ffffffff803d27c0>] (acpi_irq+0x0/0x2b)
[    3.784504] Disabling IRQ #9

Both that kernel ("Ubuntu 8.10, kernel 2.6.27-**[COLOR="Red"]11[/COLOR]**-generic") and its recovery mode come across the same problem.  Right now I'm using a second kernel ("Ubuntu 8.10, kernel 2.6.27-[COLOR="Red"]**7**[/COLOR]-generic") I somehow installed, which works fine.

According to the Ubuntu Wiki, I could "Boot the system with the "irqpoll' kernel parameter."  "This may be a workaround for an "irqXX: nobody cared . . ." error which basically means the interrupt has not been handled by any driver. This boot option will make the kernel poll for interrupts to try to work around this issue. However, this does not help diagnose the root cause nor should it be a permanent fix."  I tried it, and either I failed at doing it or it didn't help.  Regardless, how can I get a permanent fix?

---

### Post by BlueCanary9999 on 2009-04-10
bumpity?

---

### Post by BlueCanary9999 on 2009-04-11
Anyone?  Please with a cherry on top?

---

### Post by BlueCanary9999 on 2009-04-13
I hate bumping topics, but I'd really like to get that kernel working....

---

