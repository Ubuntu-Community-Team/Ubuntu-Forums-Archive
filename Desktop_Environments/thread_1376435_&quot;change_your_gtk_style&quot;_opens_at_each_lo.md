---
title: "&quot;change your gtk style&quot; opens at each login (repost with more descriptive title)"
date: 2010-01-09
forum: Desktop Environments
---

### Post by fsando on 2010-01-09
Original thread by emerger
[http://ubuntuforums.org/showthread.php?p=8635314](http://ubuntuforums.org/showthread.php?p=8635314)

A google search gives one hit (that thread) so I repost this in the hope that a more descriptive title will increase the probability of an solution.

> **emerger said:**
> I'm running Kubuntu 9.10 and I get a "Change you GTK style window" when I switch between applications with Alt+TAB. It's a strange looking window with some widgets packed into the window. If I close the window the KDE crash handler pops up.

Anybody else getting this?

Ciao.

---

### Post by David1991 on 2010-01-18
Hello

First: I am new in this forum!

I had the same problem on my kubuntu 9.10. So I looked for the autostart directory... I checked the KDE-Autostart directory in ~/.kde where I didn't find anything.

But I found out, that in /etc/xdg you can find another "autostart" directory, so I looked in it. There I found the file "gtk-kde4.desktop". I removed it and now this ugly window doesn't open anymore! :D

But maybe the file has a similar name. Don't forget to open Dolphin/Konqueror with kdesudo. Else you're not able to remove this file.

---

