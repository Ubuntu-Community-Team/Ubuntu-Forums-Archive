---
title: "Hardware management, xorg.conf and Ibex"
date: 2009-02-23
forum: General Help
---

### Post by frith on 2009-02-23
Not sure if this is a 'General Help' or 'Absolute Beginner' question, but here goes:

I installed Ubuntu for the first time about a year ago (Feisty IIRC), and spent a little while getting all the various hardware on my laptop (Toshiba portege m200) to work. Mostly the time was spent fixing things I broke trying to get some obscure things to work properly (like playing with the monitor settings broke the pen input, etc.)

Doing this, I started to get a pretty good grasp of what xorg.conf does and where to look for help with it.

Now apparently it has changed to a HAL or something (I'm not even sure where to find the documentation on what the display manager uses for hardware management!) and I am really quite lost.

When it all works (which is most of the time) its all quite nice. But there are a couple things that don't work, and I'm wondering where to look for more info.

1. The stylus doesn't work if auto-logon is enabled.
2. If the tablet goes to sleep (switch off backlight) then the stylus calibration is way off (like 4 inches) when it wakes up again.
3. I sometimes use a logitech trackball. I used to be able to hold a button and use the ball as a scroll wheel. Now apparently there is some new way of doing this (besides hacking xorg.conf) and I don't know how to find out about it.


I'm sure the new thingy is much better, but I just don't know where to find the documentation/information on it.

Anyone more knowledgeable like to share some info?

---

### Post by beno1990 on 2009-02-23
The HAL is basically a software layer which masks the underlying hardware from software so it can use all hardware much the same way regardless of what it actually is.

Anyway, it sounds like the HAL isn't starting on boot.

Try the following and tell me what it outputs:

```

sudo /etc/init.d/hal start

```

If the HAL isn't already started, it seems like something is going wrong during the boot process, maybe it's not included in the boot process, or at the wrong point.

Go into the folder /etc/rc2.d (assuming your default runlevel is still 2, which is the Ubuntu default). Once in there, confirm that a link called "S24hal" exists.

If the number following the S isn't 24, rename it to have a 24 instead.

If it doesn't exist, add it with the following command:

```

sudo ln -s /etc/init.d/hal S24hal

```

Let me know if this works for you.

---

### Post by frith on 2009-02-24
Hmmm... not sure what happened here, perhaps one of the recent updates changed something.

Now it won't automatically log on (click 'enable automatic logon' does nothing) but if I do 'enable timed logon' and set the timer for 10s (the minimum) everything seems to work. 

I guess I'll just live with it for the time being...

---

