---
title: "Lock Resolution to 1360 x 768"
date: 2008-05-04
forum: Desktop Environments
---

### Post by SauRoN ZA on 2008-05-04
Hello!

I'm currently using a Samsung 32-inch R81 LCD TV as my monitor which has a native resolution of 1360x768.

Problem is that certain applications, such as Guild Wars through Crossover/Wine for instance pumps up the resolution to 1920 x 1080 when exiting the application, which results in me having to change it back to the native resolution every time with some effort.

Now what I would like to do, is either restrict the system to the one resolution only, or just disable all resolution higher than 1360x768.

Can anyone help? Or provide an alternative?

I've read a lot of people struggle to GET 1360x768 in the first place, mine works just fine, I just don't want the rest.

---

### Post by opyate on 2009-12-05
I'm not entirely sure if this will work, but try adding:

xrandr --rmmode 1920x1080_60.00

to the end of:

/etc/gdm/PreSession/Default

Or if you have /etc/X11/xorg.conf see if the mode is in there and remove it.

I'm aware that 9.10 does not have an xorg.conf, but if you do, kindly paste/attach it here.

---

