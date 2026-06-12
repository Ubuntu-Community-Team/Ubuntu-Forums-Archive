---
title: "Updates / Changing Xorg Settings"
date: 2006-01-14
forum: General Help
---

### Post by sentient_toast on 2006-01-14
Hey guys.
I think I read somewhere that if I change xorg.conf, I won't be able to get automatic updates. If that's true, is it a big deal, and is there any work-around for it?

By the way, I've been dual-booting Ubuntu for about a month, and I gotta say this is hands-down the best Linux distro my hard drive has ever touched. I don't think it's going to be very long before I don't need Grub anymore, if you know what I mean. ;)

---

### Post by super on 2006-01-14
as far as i know, that is not entirely true.
if you manually change xorg.conf *and* you are using the *nvidia-glx* package, you will not be able to automatically update the *nvidia-glx* package.

even so, it's really not a big deal. you can update the package and make the any neccessary xorg.conf changes by hand.

---

