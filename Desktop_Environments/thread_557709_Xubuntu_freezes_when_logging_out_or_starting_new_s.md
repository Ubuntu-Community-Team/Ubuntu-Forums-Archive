---
title: "Xubuntu freezes when logging out or starting new session"
date: 2007-09-23
forum: Desktop Environments
---

### Post by cinematography on 2007-09-23
When I try to log out or start a new session, Xubuntu 7.04 freezes; the screen goes black, I can't reboot with ctrl-alt-del, restart the desktop with ctrl-alt-backspace, or switch to a different screen with crtl-alt-f2, f3, and so on. I've done a Google search and discovered this was a popular [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/112518") others have encountered. I was wondering if there was a quick fix available to repair this.

Any help would be greatly appreciated.

I'm using a Compaq Presario SR2150NX
Intel Celeron D Processor 356
ATI Radeon Xpress 1100

---

### Post by HokeyFry on 2007-09-23
umm this happened to me when i messed with my xorg.conf file. luckily i backed it up and was able to restore the original settings.

is this on a fresh install, or have you done anything to xorg.conf

---

### Post by HokeyFry on 2007-09-23
wait i read ur post more closely, its on logout...

so does this mean you can initially log in? if so, once logged in, what does pressing ctrl+alt+backspace do?

---

### Post by cinematography on 2007-09-24
Its a fresh install. I can log in just fine, but I can't start new sessions or log out. When I try Xubuntu freezes on a blank / black screen. ctrl-alt-backspace is suppose to restart the desktop, but that command, and no others, work when it freezes.

---

