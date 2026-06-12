---
title: "Power saving mode without hibernating"
date: 2009-03-15
forum: General Help
---

### Post by jamesclayden on 2009-03-15
I normaly leave my computer on all day. Is there an easy way to save some power without hibernating the computer. I was thinking turning off lan,graphics card, sound card, hard drives and only resuming to normal mode on a click.
i don't seem to have a suspend mode in 8.10 if that is what the suspend mode does how do i activate it?

---

### Post by miegiel on 2009-03-15
> **jamesclayden said:**
> I normaly leave my computer on all day. Is there an easy way to save some power without hibernating the computer. I was thinking turning off lan,graphics card, sound card, hard drives and only resuming to normal mode on a click.
i don't seem to have a suspend mode in 8.10 if that is what the suspend mode does how do i activate it?
Set your display to sleep, go to Preferences > Power management. This turns off your screen and your graphics adapter will use a lot less power.

---

### Post by sdennie on 2009-03-15
Turning off the LCD shortly after the screensaver comes on can make a significant difference in the amount of power used by the machine but, if that is not enough, you can take more extreme measures.  Have a look at [www.lesswatts.org](www.lesswatts.org) and a laptop power savings guide like this: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773").  Instead of scheduling the power savings to happen based on AC/battery power, incorporate these ideas into a simple daemon that detects if the screen saver is on and act accordingly.

---

### Post by jamesclayden on 2009-03-16
sdennie: that looks like the kind of thing that i want to do. I am not really sure how to right a daemon as i am new to linux, has no one else do this kind of thing as an application? is there a decent guide to righting the kind of daemon that i would need.

Thanks

---

