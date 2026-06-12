---
title: "new install , can't enter inside"
date: 2006-02-28
forum: Desktop Environments
---

### Post by manchette on 2006-02-28
Hi all,
i just installed Breezy but can not log in for i ain't got no more keyboard nor mouse at the log in screen
where is this coming from?
can you help please?
thanks

---

### Post by Ramses de Norre on 2006-02-28
Does the keyboard work in a shell? (alt+ctrl+F1).
Is it a special keyboard? (wireless or something?)

---

### Post by manchette on 2006-02-28
i tried with : (keyboard+mouse) 
- wireless : Genius Twintouch Luxemate
- with a wire : USB Fujitsu Siemens


>Both do work with Windows XP and SUSE 10.0
But ... do Not on with Breezy (even using ctrl+alt+f1 do not work )

(i'm using triple boot : Xp/SUSE/Breezy)

i guess it's an x server bug or sthg, i went to the x.org site, can't find any interesting wiki or discusion list...

how do i 've access to the X server ?
how do i edit etc/x11/xorg.conf ?(i can do that from Suse , for example)

---

### Post by taurus on 2006-02-28
Hold down <Ctrl><Atl>F1.  Log in from that login screen and run

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf

```

---

### Post by manchette on 2006-02-28
well, i held down, and down again
but the fact is the keyboard is not working so you can hold down it does not work

---

### Post by wrtrdood on 2006-02-28
Is it USB?  I've had problems on a Dell with the USB mouse and keyboard dropping out.  Just unplug it for a few seconds then plug it back in and it should be recognized.  It's probably a BIOS setting that's causing the problem if this is the case.

---

### Post by manchette on 2006-02-28
yes it is USB
i ain't got nothing but USB available on my pc,
i'll try your tip
why is bios ko then while working for SUSE ...and Xp ?  ( oops  :-#  )

---

### Post by manchette on 2006-02-28
usb legacy support is ok in bios (enabled)
i plugged out the sender part, then plugging it again, 
the sender led of the wifi system (mouse&keyboard) became green :D

but still no move of the mouse, nor anything while typing on keyboard :-?

---

