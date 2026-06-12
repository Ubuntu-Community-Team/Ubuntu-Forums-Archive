---
title: "Nautilus automatically re-mounts pendrive after unmount, but only once"
date: 2011-04-24
forum: Desktop Environments
---

### Post by vatzec on 2011-04-24
Hello!

I'm wondering about an issue I'm having, to which I'd like to ask you if you have a solution? What happens on my computer is this: when I insert my Walletex business card-shaped pendrive into any USB port, everything works fine, and so does unmounting using the right-click "Eject" option.

However, when I try to unmount the device using the other context menu option, "Remove device safely" (or something like that; sorry, I'm using a localized version of GNOME), it does unmount it, but then mounts it right back on. The weird thing is that after it does it, if you try using that same unmount option again ("Remove safely"), it actually works! And I can replicate this issue every time: the "Eject" context menu option works the first time every time I try it, but the "Remove safely" one, when used for the first time per device insertion causes an unmount and then a re-mount, and works the second time you try it.

Do you know what might be the cause of this?

---

### Post by coffeecat on 2011-04-24
Let me guess. You are using Maverick/10.10 and your machine has a nvidia chipset? If yes to both, this is a known nautilus bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/624755](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/624755)

In fact, if yes to the nvidia chipset. It's still happening in Natty.

---

### Post by vatzec on 2011-04-24
> **coffeecat said:**
> Let me guess. You are using Maverick/10.10 and your machine has a nvidia chipset? If yes to both, this is a known nautilus bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/624755](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/624755)

In fact, if yes to the nvidia chipset. It's still happening in Natty.

I am both using Maverick and Nvidia hardware! :-) Thanks, it's good to know it's already been reported.

Cheers!

---

