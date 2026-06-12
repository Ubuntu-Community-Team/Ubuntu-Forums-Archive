---
title: "Left click disabled after a couple minutes"
date: 2011-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by amerninja13 on 2011-07-15
Hello,

I'm running Ubuntu 11.04 on a Dell Inspiron 1440, it  has a 64-bit processor. 

Minutes after logging in (time varies from 2 to 10 minutes each time), my left clicking stops working. My laptop's touchpad is broken, so I use a Dynex Wireless Optical USB mouse, however I've seen other people having the same problem with built-in touchpads.

Using the following works temporarily:

```

xinput list
xinput set-int-prop %built_in_touchpad_id% "Device Enabled" 8 0
xinput set-int-prop %usb_mouse_id% "Device Enabled" 8 1

```

The first command lists all hardware devices, including their IDs. The other 2 disables the built-in touchpad, and enables the USB mouse once again. After executing this however, Ubuntu returns me to the login screen. After logging in my left click works.

It's kinda annoying having to do that everytime I log in to my computer, if I set the script to run whenever I login it would just log me back out (as I said above). Is there any permanent solution that wouldn't require setting a startup script?

---

