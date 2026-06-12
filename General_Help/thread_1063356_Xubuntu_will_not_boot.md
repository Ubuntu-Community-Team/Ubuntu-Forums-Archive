---
title: "Xubuntu will not boot"
date: 2009-02-07
forum: General Help
---

### Post by Mattman5465 on 2009-02-07
Hello everyone, One of my friends recently gave me a very old pc (a compaq presario 5000) And it had windows xp on it and ran very, very slow. It has an old intel celeron 568mhz and 256mb of ram, I figured instead of reinstalling xp on it, I would give xubuntu a try (hey, if it gives me more performance why not)

But it wont boot. The live cd boots, i tell it to start, and the xubuntu logo appears and progress bar below it. the progress bar goes back and forth for a while, and then loads a little bit and then stops. I left it there for 30mins just to see if it was taking a while but it just hangs there, i have tried tons of times.
I would really like to put a higher performance os in this pc. Is my hardware compatible with this distro or should I just try another one?

---

### Post by taurus on 2009-02-07
Try using the alternate CD to install Xubuntu on your machine.

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by spiderbatdad on 2009-02-07
It is possible your cd is no good, but just as likely some simple boot options might be required. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I would try noapic nolapic first...if that doesnt work, just acpi=off

sorry I don't know how to be more exact as to choice of options.

Ah yes...or alternate cd...there is a screencast too.[http://screencasts.ubuntu.com/Installing_Xubuntu](http://screencasts.ubuntu.com/Installing_Xubuntu)

---

### Post by Mattman5465 on 2009-02-07
> **spiderbatdad said:**
> It is possible your cd is no good, but just as likely some simple boot options might be required. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I would try noapic nolapic first...if that doesnt work, just acpi=off

sorry I don't know how to be more exact as to choice of options.

Ah yes...or alternate cd...there is a screencast too.[http://screencasts.ubuntu.com/Installing_Xubuntu](http://screencasts.ubuntu.com/Installing_Xubuntu)

I tried the noapic nolapic and acpi=off, no luck still hangs in the same spot. And I even tried installing with the alternate iso, still hangs at the same spot.

---

### Post by taurus on 2009-02-07
There are a few options/steps you need to take to ensure a successful installation.

1.  Run the checksum to check the integrity of the ISO image.
2.  Burn it at a slow speed like 4x.
3.  At the initial menu, run the check cd for defects to make sure the cd is good.

---

### Post by Mattman5465 on 2009-02-07
> **taurus said:**
> There are a few options/steps you need to take to ensure a successful installation.

1.  Run the checksum to check the integrity of the ISO image.
2.  Burn it at a slow speed like 4x.
3.  At the initial menu, run the check cd for defects to make sure the cd is good.

All the disks seem to be non corrupt :(

---

### Post by hellion0 on 2009-02-07
Try eliminating the splash, so that it reverts to a text boot. Just remove "splash" from the boot options (I think). That may give you a better idea at least of where the CD boot is hanging.

---

### Post by Mattman5465 on 2009-02-07
> **hellion0 said:**
> Try eliminating the splash, so that it reverts to a text boot. Just remove "splash" from the boot options (I think). That may give you a better idea at least of where the CD boot is hanging.

I have never used linux before, so i do not know what any of this means. but this is where it hangs: 

[[IMG]http://img87.imageshack.us/img87/5121/splash2sx3.jpg[/IMG]](http://imageshack.us)
[[IMG]http://img87.imageshack.us/img87/splash2sx3.jpg/1/w640.png[/IMG]](http://g.imageshack.us/img87/splash2sx3.jpg/1/)

---

### Post by Mattman5465 on 2009-02-08
bump

---

### Post by spiderbatdad on 2009-02-08
try deleting "quiet splash" and using this:```
console=ttyS0,115200 console=tty0

```
If this works you will need to edit the /boot/grub/menu.lst file after installation. More here on soft lock ups:[http://www.av8n.com/computer/htm/kernel-lockup.htm](http://www.av8n.com/computer/htm/kernel-lockup.htm)

---

