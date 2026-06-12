---
title: "Firefox and ati video driver"
date: 2009-01-14
forum: General Help
---

### Post by jasonmh on 2009-01-14
I have Ubuntu 8.10, Firefox3, and activated the ati video driver in /etc/X11/xorg.conf.  Since putting in the ati driver, Firefox won't exit a Full Screen type mode, so it's covering up my Applications menu and the taskbar. Does anyone know how to make Firefox act... normally lol I'm having to press ALT+F9 every time I want to access something outside of Firefox. [IMG]http://www.geocities.com/biocdkt/screenshot.jpg[/IMG]

---

### Post by jasonmh on 2009-01-15
I did a "sudo dpkg-reconfigure xserver-xorg" and I guess the ati drivers have nothing to do with it.  Firefox is just being stupid. So the questions stands, why is Firefox in this permanent full screen mode (it's not actually full screen, F11 does nothing).

---

### Post by zika on 2009-01-15
try:System->Preferences->CompizConfig_Settings_Manager->Utility->Workarounds->**uncheck**_Legacy_FullScreen_Support

---

### Post by jasonmh on 2009-01-15
Thanks :) I didn't have Compiz installed, so I installed it. I didn't have to do what you suggested because something in that program fixed the issue. I can now maximize Firefox without it going into that almost fullscreen mode. How weird!

---

