---
title: "Incorrect keyboard shortcuts behaviour"
date: 2009-07-12
forum: Desktop Environments
---

### Post by kubaz on 2009-07-12
Hello,

I use a very sophisticated keyboard layout that I created as whole xkb map description which I compile using xkbcomp (for easiness of use on more computers). However, after setting this map using xkbcomp mapfile $DISPLAY, global keyboard shortcuts in KDE or Gnome stop working. For example, if Win-m is the shortcut for going to the next window, then, after xkbcomp, m letter moves and the Win-(new)m doesn't work anymore. The only way I found to make it work again is to set it to something different and then set it back to Win-m.

I therefore ask - is there any way to force KDE and Gnome to reload keyboard shortcuts? If not, how can I load my map before KDE or Gnome loads their shortcuts?

Thanks,

Jakub Marian

---

### Post by kubaz on 2009-07-13
Oh, nevermind. I tried it by adding the script to Autorun as "pre-KDE Startup", but there's some bug, which I now noticed, that causes it to add it as normal Startup, but it doesn't show that until I close and open system settings again. So I copied the script manually into ~/.kde/env and am enjoying my precious keyboard layout as well as keyboard shortcuts... :)

---

