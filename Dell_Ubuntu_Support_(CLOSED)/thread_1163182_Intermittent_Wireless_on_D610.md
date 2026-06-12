---
title: "Intermittent Wireless on D610"
date: 2009-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Herbie72 on 2009-05-18
I have a Latitude D610 and have just installed Ubuntu 9.04 on it.  However, it only recognizes the wireless card intermittently upon boot up.

The card is an Intel Pro/Wireless 2915ABG, which I understand Jaunty has native drivers for.  When it works, it works great!  But when it doesn't...

I'm assuming the problem is related to a message at boot up.  The occasions when the wireless card DOESN'T work are preceded by a message referring to a PCI hardware address which reads in part "...unknown header type 7f, ignoring device."  The wireless card is a mini-PCI version.  So I'm thinking the issue is somehow tied to this.

BUT, I can't figure out how to overcome it.

No matter whether the wireless connection itself is working or not, when I type "lshw -C network" the hardware is always recognized as a network controller present on the system.

I'm a new forum member, so hopefully this will provide the information folks need to at least point me in the right direction for a solution.  Many thanks for any and all thoughts.

---

### Post by Herbie72 on 2009-05-18
A new wrinkle now.  When the wireless card DOES function, I'm having the touchpad cursor lock up.

---

