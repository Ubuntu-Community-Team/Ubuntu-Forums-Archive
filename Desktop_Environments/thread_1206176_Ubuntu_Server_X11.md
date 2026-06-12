---
title: "Ubuntu Server X11"
date: 2009-07-06
forum: Desktop Environments
---

### Post by patrickweber on 2009-07-06
I'm running ubuntu server on a test machine here and love to use the CLI (don't want to use a WM).  The main problem I have with it though is that the resolution of the screen is so low and so little text fits on the screen that it's hard to use.

So, I installed X11 and fired it up.  It automatically found the resolution of the screen and set it up appropriately.  The main problem is that although the screen resolution is higher, the size of the terminal window up in the upper left hand corner is still the regular tiny window size which really doesn't help at all, except for making the fonts smaller on screen.

Is there any way I can increase the size of the little terminal window and if possible center it on screen?

---

### Post by wojox on 2009-07-06
Edit /boot/grub/menu.lst to change the resolution.

Look for vga=791 or what ever number after defoptions.

Update grub:

sudo update-grub

---

### Post by patrickweber on 2009-07-06
So I can do it independent of X11?

Also, I can't find anywhere that says vga= in my menu.lst file.

---

### Post by wojox on 2009-07-06
Sorry here it is

```
cat /etc/default/console-setup
```

I had to log into my server and find it.

then just open it in your editor of choice.

---

### Post by patrickweber on 2009-07-06
Actually, your first method works.  Unfortunately, my framebuffer only supports a max resolution of 1280x1024, so it's not my full screen resolution.  I suppose it's better than the 640x480 :).

Your second piece only changes the font size, not the screen resolution.

Thanks!

---

