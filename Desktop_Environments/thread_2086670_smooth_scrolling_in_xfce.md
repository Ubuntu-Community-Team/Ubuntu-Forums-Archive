---
title: "smooth scrolling in xfce"
date: 2012-11-21
forum: Desktop Environments
---

### Post by shvx on 2012-11-21
I'm using Xubuntu 12.10 on an HP Pavilion dm1 and wondering what's up with the smooth-scroll behavior.

Let's say I try to use two-finger scrolling in the Document Viewer while looking at a PDF. If I scroll while the pointer is on top of the document, i.e. in the middle of the window, I don't get smooth behavior. The page just acts the way it used to before smooth scrolling existed.

However, if I put my pointer on top of the scrollbar on the right side and try to use the trackpad to scroll, smooth scrolling works, and it works great! No more jumpy pages or anything.

My question is: why is smooth scrolling only half-working and how to I fully enable this functionality so that I don't always have to carefully position my pointer over the scrollbar (what's the point of even having two finger scrolling if I have to go to the scrollbar anyway?).

Thanks in advance.

edit: I should add that smooth scrolling doesn't work at all in Chromium without installing the Chromium Wheel Smooth Scroller extension; but I already understand why Chromium works like that.

---

### Post by cwsnyder on 2012-11-21
I take it you are using a touch screen?  You should state so in your posting.

---

### Post by LewisTM on 2012-11-21
Seems this bug has been reported before
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/981248](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/981248)
Apparently they are working on a patch for Evince.

Cheers!

---

### Post by rai4shu2 on 2012-11-21
Seems to be a GTK bug. I wonder if Qt apps work with smooth scrolling?

---

### Post by LewisTM on 2012-11-21
> **rai4shu2 said:**
> Seems to be a GTK bug. I wonder if Qt apps work with smooth scrolling?
Never really paid much attention but most GTK3 apps have smooth scrolling whereas GTK2 apps don't.
Dolphin has it on but not Okular, both KDE apps. Maybe it needs to be controlled elsewhere?

---

### Post by shvx on 2012-11-21
> **LewisTM said:**
> Seems this bug has been reported before
[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/981248](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/981248)
Apparently they are working on a patch for Evince.

Cheers!

Ah, thank you. That bug report explains a real lot. Looking forward to seeing that patch released.

From what I can tell smooth scrolling is a GTK3 feature but Evince uses a custom document view that doesn't implement the GTK_SCROLL_SMOOTH event. This also explains why smooth scrolling works in Nautilus but not in Thunar.

---

### Post by dentaku65 on 2012-11-23
Edit/create in this file with nano:
```
nano ~/.gtkrc-2.0 
```
These customizations:
```
gtk-menu-popup-delay = 0
gtk-menu-popdown-delay = 0
gtk-menu-bar-popup-delay = 0
gtk-enable-animations = 0
gtk-timeout-expand = 10
```

Save and reboot

---

