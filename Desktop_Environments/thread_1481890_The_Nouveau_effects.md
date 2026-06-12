---
title: "The Nouveau effects"
date: 2010-05-13
forum: Desktop Environments
---

### Post by nicolasdiogo on 2010-05-13
Hi folks,

i have installed Lucid on my old T61p. and i am using the NVidia driver Nouveau.

But i can not work out how to enable compiz with it.

is it possible to have composite effects with this driver?

thanks,

Nicolas

---

### Post by infamous-online on 2010-05-13
> **nicolasdiogo said:**
> Hi folks,

i have installed Lucid on my old T61p. and i am using the NVidia driver Nouveau.

But i can not work out how to enable compiz with it.

is it possible to have composite effects with this driver?

thanks,

Nicolas

If your viedo card is low graphics then it won't work sadly. It only works with graphic cards with a fairly amount of memory I'm afraid. What are your specs on your video card?

---

### Post by 3rdalbum on 2010-05-13
The Nouveau driver that comes with Ubuntu is 2D only and can't run Compiz.

You can compile the latest Nouveau driver and get some experimental 3D support, but you might as well use the proprietary Nvidia driver; it's probably going to be more stable and more bug-free.

---

### Post by nicolasdiogo on 2010-05-30
hi,

i gave up on nouveau for now and went back to nvidia drivers.

but even those did not provide effects at first.

there seems to be a bug with Lucid Jockey driver.

when installing jockey it install some old nvidia drivers as requirements and these interfere with the latest nvidia driver.

so you will have to open synapitcs and remove any nvidia package that is not the latest (search for nvidia)

in my case i uninstalled every thing that was not nvidia 185 and jockey-gtk, and jockey.

with the old driver i was getting the following error:

```
Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
```

you can use this script to assist you in troubleshooting:

[http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

hope this helps other solving this problem.

thanks

Nicolas

---

