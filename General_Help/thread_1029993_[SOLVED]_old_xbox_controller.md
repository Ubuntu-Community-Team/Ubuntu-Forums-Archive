---
title: "[SOLVED] old xbox controller"
date: 2009-01-04
forum: General Help
---

### Post by oneadvent on 2009-01-04
I have an old xbox controller, I spliced the cables and made it a usb cable, as many have, and it works on Windoze well enough. 

It shows up in lsusb, but jscalibrator doesn't see it, and it doesn't show up in /dev/input either.

Support for this should be in by default, so what am I doing wrong?

---

### Post by Tim Sharitt on 2009-01-04
You may want to look at this page to see if it helps any.
[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

---

### Post by oneadvent on 2009-01-04
I had taken a look there first. (I try to do some research before bugging the gurus :) ) However, the only section that deals with old xbox controllers says this:

> When dealing with the older Xbox™ controllers, all you need to do is to make, or obtain, a USB adapter and plug it in; driver support for the older controllers should already be installed and active. If the controller doesn't respond, see the Testing and Troubleshooting section. 

And the trouble shooting section basically says reinstall the kernel mod if it doesn't work. I didn't have to install a kernel mod, so the circular reasoning didn't get me anywhere.

I think it has something to do with it not showing up as js0 in /dev/input/, I just dont know how to fix it.

---

### Post by oneadvent on 2009-01-04
I finally got it working with this mans awesome post: 
[http://ubuntuforums.org/showthread.php?t=825464](http://ubuntuforums.org/showthread.php?t=825464)

It works with the old xbox and the xbox 360 controllers.

I will mark this as solved and hope someone runs across it in the future.

Also: I bawk that it was said that it is built in support. No such support was built into MY box. Humph.

and now to get the triggers working...

---

