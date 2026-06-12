---
title: "Loss of mouse click ability when window gains inner focus"
date: 2011-01-11
forum: Desktop Environments
---

### Post by SSzretter on 2011-01-11
This morning on my Ubuntu 10.10 system when I open a window - for example, system->preferences->about me, if I click in to a field such as "work email", I can no longer close the window with the mouse! Clicking the X on the window will not work.

Also, I loose the ability to click on anything else - clicking on the desktop, icons, menus, workspaces, etc. do not work. Even the effect when you hover over a folder on the desktop and that folder highlights - that stops until the window is closed.

If I open this same screen but do not click in to a field, everything is fine - I can close the window with the X and everything else works fine.

Same thing happens with several other windows I tried. Even calculator - I can open it, everything is fine until I click on a button in the calculator - then no ability to click on anything else. Have to Alt-F4 to close the window.

The system is only about a week old from a fresh install (64 bit ubuntu - quad core amd machine).

I uninstalled wine, turned off remote desktop/disabled in startup, also in startup disabled visual assistance, bluetooth, dropbox, klipper. Reboot, no difference.

The only other thing non-standard I see in startup is nvidia.

Using a logitec usb mouse, saitek usb keyboard.

Was working fine yesterday. I can not think of anything I did / installed yesterday.

I switched themse, then went to update manager and saw two x server / x org related updates and installed them, reboot and NOW IT IS FINE!

However, then I re-enabled dropbox, klipper and remote desktop rebooted and the problem is back. Again I disabled those and rebooted. Problem is still there!!

So somehow I fixed it at least for a few minutes, but now it is back and I am out of ideas.

---

