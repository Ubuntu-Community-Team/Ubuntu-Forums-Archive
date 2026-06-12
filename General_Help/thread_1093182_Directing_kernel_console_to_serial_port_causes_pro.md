---
title: "Directing kernel console to serial port causes problems"
date: 2009-03-11
forum: General Help
---

### Post by maddis on 2009-03-11
I noticed that directing kernel console to serial port causes all sorts of problems. 

First that I noticed was that splash screen isn't shown anymore during bootup. Instead following error is shown in console:

splash: libusplash.c:289: switch_console: Assertion `(saved_vt >= 0) && (saved_vt < 10)' failed.

Second, more strange, problem is that USB sticks aren't mounted automatically anymore. When connecting the USB stick I can see that unit founds it just find and I can see that USB stick is accessed, but it won't get mounted anymore.

All this by just to adding 'console=ttyS0,115200' to the end of the kernel - line in /boot/grub/menu.lst. Console itself works just fine.

Any idea how to get splash screen and automount to work _with_ the serial kernel console?

---

