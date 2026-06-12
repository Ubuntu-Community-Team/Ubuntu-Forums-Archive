---
title: "Xwindows stopped working"
date: 2012-07-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jflinux on 2012-07-27
On my Dell 1557 studio, X does not start anymore as of my last reboot yesterday July 26, 2012.   It gets to the splash screen where the dots change color as it is booting.  I run 1920x1080 on the laptop with unity ubuntu 12.04.

This seems to be due to the automatic updates to ubuntu in the last week.

If I boot to an older version of the kernel in the Grub selection menu or
to the recover mode, X works fine.

---

### Post by Laiquendi on 2012-07-27
Radeon drivers.
Have you installed the proprietary driver? If yes, then it may crash on every kernel update.
Solution is to re-install (by command line in recovery mode or by virtual-console) the driver. And never again use ati.

---

### Post by jflinux on 2012-08-01
Thanks for the tip.  Strangely enough, it seems to be working now
without me doing anything???  If it happens again,
I'll try your fix.   Maybe this is an intermittent problem with X?


> **Laiquendi said:**
> Radeon drivers.
Have you installed the proprietary driver? If yes, then it may crash on every kernel update.
Solution is to re-install (by command line in recovery mode or by virtual-console) the driver. And never again use ati.

---

