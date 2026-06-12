---
title: "Prevent the xorg from catching a HID"
date: 2009-01-28
forum: Desktop Environments
---

### Post by cheerybounce on 2009-01-28
I have a 3DConnexion mouse on ubuntu intrepid, which seems to work fine when I put: Option "AutoAddDevices" "False" into ServerFlags -section into my xorg.conf, after I modify the udev to understand it as a joystick HID.

But certainly this causes other trouble with my other HID devices that behave correctly. For instance my apple flat keyboard doesn't like this flag.

The problem is that the 3DConnexion spacenavigator gets grabbed by xorg and virtualized into a two-axis mouse.

How can I prevent xorg from grabbing just the spacenavigator mouse or otherwise just get it freed from XInput?

---

