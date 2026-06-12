---
title: "Laptop - Dual Head - Gnome Panel Placement"
date: 2008-10-29
forum: Desktop Environments
---

### Post by freelinuxhelp on 2008-10-29
Running Intrepid beta with latest updates on my Lenovo R61 laptop. When at my desk, I connect an LCD monitor to it for a larger desktop. Everything about this setup works perfectly except for the fact that the Gnome panels, top and bottom, load on the monitor - not the laptop display. I can drag them back over to the laptop, but after rebooting, they are back over on the monitor. Is there a way to lock the panels down to the laptop display?
THanks

---

### Post by freelinuxhelp on 2008-10-29
Forgot to include screenshot:
[IMG]http://freelinuxhelp.com/wp-content/uploads/2008/10/desktop.png[/IMG]

---

### Post by freelinuxhelp on 2008-10-30
Any ideas?

---

### Post by BugFreeWin on 2009-02-08
> **freelinuxhelp said:**
> Running Intrepid beta with latest updates on my Lenovo R61 laptop. When at my desk, I connect an LCD monitor to it for a larger desktop. Everything about this setup works perfectly except for the fact that the Gnome panels, top and bottom, load on the monitor - not the laptop display. I can drag them back over to the laptop, but after rebooting, they are back over on the monitor. Is there a way to lock the panels down to the laptop display?
THanks

Hello,
I think it is related to the fact, that laptop display is configured to use pipe B, and external monitor - pipe A, and if available, gnome uses pipe A.

Xorg.0.log:

(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0):   Output LVDS is connected to pipe B

---

