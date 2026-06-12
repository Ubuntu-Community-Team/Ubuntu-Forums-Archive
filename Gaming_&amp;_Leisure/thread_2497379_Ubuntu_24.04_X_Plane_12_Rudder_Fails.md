---
title: "Ubuntu 24.04 X Plane 12 Rudder Fails"
date: 2024-05-02
forum: Gaming &amp; Leisure
---

### Post by lisanels47 on 2024-05-02
This issue happened a long time ago with Ubuntu 22.04 and Xplane11.  The symptoms are that XPlane 12 sees the yoke controller, but not the rudder controller.
Within Xplane12 there's the calibaration etc., for the yoke.

Linux shows both USB devices (Yoke,Rudder) when listing usb devices; lsusb

The fix is I had to add my username to the linux group named 'input'

Then it all worked fine.

---

### Post by slovenskekasina on 2024-08-06
It sounds like you're experiencing a familiar issue with X-Plane 12 where the rudder controller isn't being recognized, despite both the yoke and rudder showing up in "lsusb".

---

