---
title: "Usplash and console output to serial port"
date: 2009-02-24
forum: General Help
---

### Post by maddis on 2009-02-24
I ran into this problem when trying to direct console output to serial port.

So for example I boot from live cd and edit kernel command line by adding console=ttyS0,115200. After this I get the console output to serialport as it should, but no more splash screen are shown. Instead I get following error to console:

> usplash: libusplash.c:289: switch_console: Assertion `(saved_vt >= 0) && (saved_vt < 10)' failed.

This happens with livecd and with system already installed on HD. Are there any way around this or is this just a feature that cannot be turned off?

---

