---
title: "login window has disappeared"
date: 2011-11-10
forum: Desktop Environments
---

### Post by mstarcrest on 2011-11-10
Since yesterday, I no longer see a login window when I boot my ubuntu box.  After the normal boot process, all I see is the standard purple gradient Ubuntu 10.04 desktop background -- nothing else, no way to select my username, enter my password, etc.  So I can't login to the desktop (but I can still ssh in, where everything seems normal).

Further oddities:  in an attempt to debug, I started to try changing my login appearance:
> sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

Then when I reboot, I see the Appearance Preferences window -- which seemed encouraging, given I previously wasn't seeing any windows at all.  I can click around on the Theme tab or Fonts tab .... but when I click on the Background tab, the Appearance Preferences window disappears!  Again, I'm back to just seeing the purple Ubuntu desktop background, nothing else.

I also tried restarting /etc/init.d/gdm, but that doesn't change anything.

This is Ubuntu 10.04.2 LTS.   Really stuck -- any ideas?

---

### Post by mstarcrest on 2011-11-11
Solved.  Here's what it was for my particular case:
[http://www.linux-archive.org/ubuntu-user/401236-no-login-screen-after-splash.html](http://www.linux-archive.org/ubuntu-user/401236-no-login-screen-after-splash.html)

"I had installed zlib 1.2.5 from source from: [http://www.zlib.net/](http://www.zlib.net/). Once I sudo make uninstall from the zlib source directory it fixed EVERYTHING from the dpkg errors to the applet errors to the login."

---

