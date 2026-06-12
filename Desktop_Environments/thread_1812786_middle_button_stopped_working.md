---
title: "middle button stopped working"
date: 2011-07-26
forum: Desktop Environments
---

### Post by n-alexander on 2011-07-26
kubuntu 11.04

the middle button does not work any more. Tested with xev - buttons 1 and 3 show up, button 2 does not.

Really miss past with middle button.

Thanks,
Alex

---

### Post by n-alexander on 2011-07-26
> **n-alexander said:**
> kubuntu 11.04

the middle button does not work any more. Tested with xev - buttons 1 and 3 show up, button 2 does not.

Really miss past with middle button.

Thanks,
Alex

..and there seems to be no xorg.conf any more in 11.04, so can't fix it there..

---

### Post by enimeizoo on 2011-07-26
Did you do something special, like upgrading distribution?
What is the output of xmodmap -pp ?

---

### Post by n-alexander on 2011-07-27
> **enimeizoo said:**
> Did you do something special, like upgrading distribution?
What is the output of xmodmap -pp ?

I did upgrade to 11.04 around the time it came out. The middle button certainly worked before upgrade, and I'm pretty sure it worked after.

I apply updates periodically, so not sure if a particular update broke it.

I also blacklisted some modules that otherwise conflicted with my USB Wifi stick. Now that I check, I see that /etc/modprobe.d/blacklist.conf has been overwritten, probably by an update, and now has this in it:

```
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
```


```
~: xmodmap -pp
There are 16 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9
       10             10
       11             11
       12             12
       13             13
       14             14
       15             15
       16             16

```

---

### Post by enimeizoo on 2011-07-27
Well, the xmodmap config is just fine, so this is more likely a problem at kernel level. Can your restore the blacklist file the way you wrote it? 
I'm not an expert, but the blacklisted usbmouse module looks suspect :P . Is it one of the modules that conflicted with your usb stick?

---

### Post by n-alexander on 2011-07-28
> **enimeizoo said:**
> Well, the xmodmap config is just fine, so this is more likely a problem at kernel level. Can your restore the blacklist file the way you wrote it? 
I'm not an expert, but the blacklisted usbmouse module looks suspect :P . Is it one of the modules that conflicted with your usb stick?

restoring does not make a lot of sense - I blacklisted some drivers that conflicated with Wifi chip. The mouse worked before and after that.

I allowed the mouse and loaded the driver but it didn't help

---

### Post by enimeizoo on 2011-07-28
Actually, the xorg.conf has been split into several files, but if you create one, it will have priority over those.

Maybe have a look at /usr/share/X11/xorg.conf.d

Hope it helps

---

### Post by StephanG on 2011-07-29
Before you guys get too carried away with configuration files.  Have you confirmed that it's not a hardware issue?  Does the middle button work if you plug the mouse into another machine?

Or, does it work when you run a live CD?

If the middle button still doesn't work in those cases, I think that it might just be that your mouse is starting to show signs of wear and tear, and it might just be easier to replace it.

---

### Post by n-alexander on 2011-07-29
> **StephanG said:**
> Before you guys get too carried away with configuration files.  Have you confirmed that it's not a hardware issue?  Does the middle button work if you plug the mouse into another machine?

Or, does it work when you run a live CD?

If the middle button still doesn't work in those cases, I think that it might just be that your mouse is starting to show signs of wear and tear, and it might just be easier to replace it.

scrolling with the middle button works, so the electricity must be there

---

### Post by emaydubya on 2012-03-05
This just started for me. Was fine an hour ago. Went and had lunch now I notice it doesn't work. Reboot, same.

another dead end:

---

