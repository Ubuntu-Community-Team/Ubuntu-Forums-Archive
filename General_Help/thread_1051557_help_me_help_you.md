---
title: "help me help you"
date: 2009-01-26
forum: General Help
---

### Post by moose3 on 2009-01-26
Ok, I have discovered some problems as seen in my post in the wireless section: [http://ubuntuforums.org/showthread.php?t=1049595](http://ubuntuforums.org/showthread.php?t=1049595) and I would like someone to point me in the right direction to properly submit this bug. (I am new to ubuntu/linux so please be specific)

This started with a pcmcia wireless card not working, leading to the discovery of an IR device that while disabled in BIOS was thought to be active by Ubuntu, causing an IRQ conflict.  Activating the card and setting it to a different IRQ in BIOS than what Ubuntu wanted to use caused a Kernel crash, and enabling it but with a different DMA in BIOS than Ubuntu expected caused it to be disabled, making a viable workaround to the problem of a wireless card not working for me, but pointing out a bug that needs to be checked.  If this happens here, it might be a deeper coding error that affects others if the system is supposed to be more flexible in checking the BIOS, and assigning resources.

Thanks

---

### Post by utnubuuser on 2009-01-26
Ubuntu bugs at launchpad.net> [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by plucky on 2009-01-27
See the **sticky** in Absolute Beginners Talk [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)


Good Luck

---

### Post by moose3 on 2009-01-27
Thanks for the links, just what I was looking for.

One of the posts mentions asking to make sure this is a bug. I'm fairly sure a bios disabled device being treated as active, as well as when configured in bios, there is a kernel panic is a bug.  Now to see if it has been reported already.

Thanks again.

---

