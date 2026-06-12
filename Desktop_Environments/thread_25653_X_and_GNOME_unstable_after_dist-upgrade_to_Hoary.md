---
title: "X and GNOME unstable after dist-upgrade to Hoary"
date: 2005-04-10
forum: Desktop Environments
---

### Post by stoneguy on 2005-04-10
The upgrade looked smooth. Aside from a new ACPI-related error that I haven't dealt with (unable to locate RSDP), I though I was home free.

But now, after using the system awhile, the desktop gets borked. Typically, windows don't get redrawn - they just go white and can't be selected or clicked. Mouse motion is OK though. (BTW, this is an onboard RageProII vidchip.)

When the system gets into this state, CTL-ALT-BKSP shuts X down, but then it's stuck some kind of a failing restart loop. Eventually you can get to a console by hammering on CTL-ALT-F1. You can't do a startx because the system thinks that :0 is still running. Only way out seems to be a reboot.

CTL-ALT-BKSP by itself if problematic even when the desktop is working. Sometimes it works fine. Other times it leaves x-session-manager running, which has to be killed before a startx will work. /etc/init.d dbus-1 restart is required to populate Places correctly any time X starts (including the 1st apparently).

 :confused:  Is anyone seeing these problems that has done a fresh install? I'm wondering whether this is a dist-upgrade artifact, or a more fundamental problem.

Added:
I decided to get rid of the RSDP message by adding acpi=off to the kernel line in GRUB menu.lst. System seems a lot more stable now  \\:D/

---

