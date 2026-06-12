---
title: "vga=791 leads to a blank screen"
date: 2009-05-10
forum: General Help
---

### Post by myyers on 2009-05-10
Some time a ago when I gave ubuntu (gutsy) a try I had this well-known problem with a non-working framebuffer. I could fix it with the also well-known workaround (insert fbcon,vesafb,vga16fb in /etc/initramfs-tools/modules, update-initramfs -u, and uncomment the appropriate modules in /etc/modprobe.d/blacklist-framebuffer.conf).
Why, now with 9.04 this does not work anymore. 
Any hints how to get it work again?

myyers

---

