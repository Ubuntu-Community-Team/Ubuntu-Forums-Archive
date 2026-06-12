---
title: "~1/5 of boots fail with a graphics corruption"
date: 2010-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by OliverN on 2010-10-17
Approx. 1 in 5 of my boot sequences looks as follows:

1. Normal grub boot screen (selecting Ubuntu)
2. Black screen except for a blinking marker at top left
3. Graphics corruption of the original grub screen, complete lockup of my pc, forcing reboot.

I'm on an Inspiron 6400 with an ATI x1400 gpu. I'm using ubuntu 10.10 with kernel 2.6.32-12-generic, 32 bit. The problem has been consistent across several different kernels, first starting ca. 6 months ago. I'm using standard drivers and have tried the fglrx drivers which won't work on my machine. I do have compiz and all that jazz when my pc does boot. The occasional lockup is pretty annoying, though. Anything that might be done about that?

---

### Post by gibbylinks on 2010-10-18
Do you use the "nomodeset" option in grub ?

Try searching the forums for it. I can't boot without it, just get stripes

---

### Post by OliverN on 2010-10-18
> **gibbylinks said:**
> Do you use the "nomodeset" option in grub ?

Try searching the forums for it. I can't boot without it, just get stripes

I haven't used anything other than the standard options. I'll try booting with it, but it'll take some time before I know if it actually solves the problem. I never got into configuring grub2 so can you also tell me how to make the boot option permanent if it should work?

---

### Post by gibbylinks on 2010-10-19
I refer back to this thread every time I need help with Grub. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) you should find what you need in there. :)

---

### Post by OliverN on 2010-10-19
> **gibbylinks said:**
> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

oh my God... If i'm not back in 3 days tell Timmy I love him...

---

### Post by gibbylinks on 2010-10-20
Ok I'll narrow it down for you. To make it permanent you need to

```
sudo gedit /etc/default/grub
```And look for the line below and add "nomodeset" as shown.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **[COLOR=Red]nomodeset[/COLOR]**"
```And then you will need to update GRUB so type

```
sudo update-grub
```And re-boot.

It's also an idea to subscribe to this thread or bookmark it, so you can find it easily. I always need to look this up every time I do a fresh install !! :P

---

### Post by OliverN on 2010-10-20
hey thanks a bunch. I couldn't figure that one out although I did get around to theming my menu nicely. Even if this doesn't work at least now I know how to investigate what does. Thanks again.

EDIT: booting with nomodeset actually seems to have solved my problem.

---

