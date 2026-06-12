---
title: "XP USB Boot problem"
date: 2010-07-13
forum: Development CD/DVD Image Testing
---

### Post by kyser on 2010-07-13
I'm running ubuntu 9,10, and I recently mounted an xp iso to my usb key using UNetBootin.

However when I booted from the USB on my formatted computer, it showed a boot menu for debian (choices, only one showing was "default"). When I hit default or let it autochoose, it takes no action and resets the autochoose counter (will auto boot in....6).

Does anyone know why I might be encountering this problem? 

(Also, I've used the .iso before and it works, but I've never mounted it to a usb using ubuntu)

---

### Post by C.S.Cameron on 2010-07-13
UNetbootin does not work with Windows.
The only method that I have found to run XP from a USB flash drive is described here:
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

---

### Post by kyser on 2010-07-13
That uses winISO, my problem is that if UNetBootin doesn't work for windows, I don't know how else to mount the iso to the usb key from ubuntu (my only option).

---

### Post by C.S.Cameron on 2010-07-13
Do you just want to make a windows install USB key?

> 1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
-> put bootable flag (right click in gparted - manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick

From Amedac

---

