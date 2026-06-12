---
title: "[SOLVED] giving Virtual Box read/write permission"
date: 2007-12-12
forum: Desktop Environments
---

### Post by zachthejones on 2007-12-12
I'm playing around with running a virtual OS in Virtual Box - I thought I'd start by trying out Puppy Linux. Everything seems to be going fine, but when I try to start it up for the first time, I get this error message:

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

I'm not sure how to do this. Where is the "vboxusers groups" and how do I cange permissions for /dev/vbox/bvoxddrv ? Is this a permission I'm going to have to set every time, or is it permanent?

---

### Post by ubukool on 2007-12-12
Hi,

Check out my reply on this thread:

[http://ubuntuforums.org/showthread.php?t=635334](http://ubuntuforums.org/showthread.php?t=635334)

Good luck! :)

---

### Post by zachthejones on 2007-12-19
Thanks a bunch! That fixed my problem, now I've got Puppy Linux booting from the ISO image...but it freezes shortly after deciding which display driver to use.  I also tried Linux Mint, but it also freezes shortly into the booting up process.

It might be my computer (an older 2.0 ghz Celeron with only 512 mb of RAM), but if you've any suggestions, they'd be greatly appreciated.

---

