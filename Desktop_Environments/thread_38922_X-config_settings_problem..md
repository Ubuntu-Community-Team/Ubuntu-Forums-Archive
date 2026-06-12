---
title: "X-config settings problem."
date: 2005-06-02
forum: Desktop Environments
---

### Post by chris_andrew on 2005-06-02
Hi,

My Kubuntu install went really really well. Unfortunately, I have a 2cm gap at each side of my Sun monitor.

When I used Deebian, in order to reconfig X, I would run

dpkg-reconfigure xserver-xfree86

It doesn't look like X is managed the same way in Kubuntu, can anybody point me in the right direction?

Seems a shame to have a 21" hi spec CRT monitor, and not be able to use the whole screen.

Thanks,

Chris.

---

### Post by Gezzer on 2005-06-02
try

sudo dpkg-reconfigure xserver-xorg

---

### Post by chris_andrew on 2005-06-03
Ah, that old trick!!

Cheers,

Chris.

---

