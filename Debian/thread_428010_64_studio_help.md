---
title: "64 studio help"
date: 2007-04-29
forum: Debian
---

### Post by rockyraccoon on 2007-04-29
hey,
i just installed 64 studio on a separate partition. when i try to boot it, it runs through the sequence and then gets to a point where the screen goes black, apparently because there is no signal. the monitor gives me an "out of range" message. i'm assuming its something to do with my video card/driver, which is an nvidia ge force 7300 gs. any ideas? i was very excited to give it a whirl.


thanks.

---

### Post by bwhite82 on 2007-04-30
This is more than likely due to an incorrect vertical and horizontal sync range in your X configuration (for your monitor). Try this at the command line:

> sudo dpkg-reconfigure xserver-xorg

---

