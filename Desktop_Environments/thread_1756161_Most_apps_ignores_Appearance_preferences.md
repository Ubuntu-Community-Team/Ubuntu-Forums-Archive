---
title: "Most apps ignores Appearance preferences"
date: 2011-05-11
forum: Desktop Environments
---

### Post by oltio on 2011-05-11
Hi,

I've just updated to 11.04, switched into the classic desktop (Unity? just say NO), disabled overlay scrollbar, and still I'm confused.

I customized the appearance preferences of my desktop to change the appearances of the widgets. I selected "Clearlooks" but most applications just ignore the preference. Here I attached a screenshot:
[IMG]http://gyazo.com/a85051ac32cf5833a82bf506a9b5136e.png[/IMG]

While the buttons in "Appearance Preferences" are round-shaped, the buttons in "Network proxy" window are square (probably it's from "Redmond" theme?)

As far as I checked, only the "Appearance Preferences" obeys the setting. Other preferences (e.g. fonts, colors, icons) are ignored too.

---

### Post by Krytarik on 2011-05-12
May it be related to this bug?:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

Recent threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Greetings.

---

### Post by oltio on 2011-05-13
Thanks. I checked the .xsession-erros and found some warnings from gnome-setting-daemon, and found this bug.

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

It seems to be my place. Thank you for your suggestion.

---

### Post by Krytarik on 2011-05-13
Yeah, that's the respective bug report, I, too, have it in my bookmarks, from now on I will link to it as well, for more clarity.

See if the mentioned workarounds help you.

---

