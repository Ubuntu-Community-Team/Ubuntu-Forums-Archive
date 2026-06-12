---
title: "Re: Gnome Top and Bottom Panel not Responding (partially)"
date: 2010-06-07
forum: Desktop Environments
---

### Post by isync on 2010-06-07
[Related to this thread from the archives]("http://ubuntuforums.org/showthread.php?t=218547").

For anyone who can file a bug report:

Today I did a fresh 32bit install of Ubuntu 10.04 and ran into the exact same issue someone reported a few years back in the above post.

What I did was:
I changed the alignment of the upper panel to bottom and then switched on auto-hide. I ended up with a non-reacting taskbar and hovering the mouse over the panel did not bring up any menues etc. Although the network-manager-icon, login/out etc on the lower right were still working.

Fix was:
I entered a shell with ALT+F2 and did *killall gnome-panel*. When I switched back into the xserver with ALT+F7 the taskbar was usable again. So I switched off auto-hide and crossed fingers that was the trigger and turning it off solves the bug for next reboot.

---

### Post by spotrick on 2010-07-08
I had that exact problem today -- leaving me with an unusable desktop. I will try your fix tomorrow when I'm back in the office. I did try a reboot (obviously) but it came back up with the same broken panel. Also, on shutdown (responding to Ctl-Alt-ESC) I got a dialog saying application "panel" was not responding.

---

### Post by spotrick on 2010-07-08
Fixed!

After Alt-F2, I edited the file .gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml

changing auto-hide to false.

Then I rebooted. And all seems to be well now.

---

