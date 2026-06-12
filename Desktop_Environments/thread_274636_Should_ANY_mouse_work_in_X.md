---
title: "Should ANY mouse work in X?"
date: 2006-10-10
forum: Desktop Environments
---

### Post by blumi00GT on 2006-10-10
Hi,

for my MediaCenter PC I am looking for a very small, nice, wireless mouse. I already spotted some, but there are of some no-name brand I never heard of.

Are there any points I should be aware of before buying some crap that will never work in X11? Or should every USB mouse simply work with the right configuration in xorg.conf?

Thanks,
Bastian

---

### Post by CatKiller on 2006-10-10
As far as I know, **with the right configuration**, any mouse will work with X11. Certainly every problem I've seen here has been incorrect configuration, rather than a mouse inherently not working with Linux.

---

### Post by chasby on 2006-10-11
I just replaced my regular PS/2 3-button mouse with a Kensington wireless 3-button on my Dapper system.  Works fine and required no configuration changes

---

### Post by elemental0125 on 2006-10-11
Any mouse (within reason) should work as long as it uses PS2 (not so commomon outside of $5 mice), conforms to the USB HID (standard inferface for Mice, Keyboards etc.) or the Bluetooth HID. In the bluetooth case you'd need to get it set up first given that (in my experience) Linux's Bluetooth support isn't always so user friendly...

---

### Post by .t. on 2006-10-11
evdev is a very good driver. It supports most input devices. Some have their own drivers with more config options, but evdev supports those as well. Most of the time input devices work outta the box.

---

