---
title: "[SOLVED] Questions about Usplash and Startup Manager on 1280x800 monitor"
date: 2008-06-01
forum: Desktop Environments
---

### Post by the8thstar on 2008-06-01
Hello all,

I have installed Startup Manager with a bunch of .so files to customize my usplash.

My laptop screen is 1280x800, which isn't listed in the options of SUM. Therefore, whenever I change the usplash (even the default Ubuntu one), my screen is all extended or worse, the splash is not centered.

So my questions are:

[COLOR="Blue"][B]1. Is there a way to set a 1280x800 resolution? I tried setting usplash.conf, but it didn't change anything

2. Do I need to edit Grub? If so, what is the VGA code for this 1280x800 resolution?

3. Is there anything else I could do?[/B][/COLOR]

---

### Post by angry_johnnie on 2008-06-02
apparently 1280x800 is not a vesa mode (seriously... I was curious about this,too, but it's just not there!), so you'll have to settle for either **vga=792** or **vga=795**, which will give you 1024x768, or 1280x1024, respectively.

---

### Post by gils0040 on 2008-06-10
If you want to get your hands dirty you could try uvesafb. It will require a kernel rebuild and an initrd but it should be able to set a resolution of 1280x800.

---

