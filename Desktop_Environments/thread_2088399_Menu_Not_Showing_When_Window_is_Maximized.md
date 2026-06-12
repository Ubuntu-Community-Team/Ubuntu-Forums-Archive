---
title: "Menu Not Showing When Window is Maximized"
date: 2012-11-26
forum: Desktop Environments
---

### Post by chazdg24 on 2012-11-26
I have removed the Global App Menu as I prefer to have the minimize, maximize, close buttons on the right side of each app. I did this with no problem in 12.04. I did an upgrade to 12.10 and noticed that Chrome, Chromium and Firefox all use the Global Menu.

I have done the following:

sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt

I have disabled the Firefox extension. I removed the corresponding Firefox package but still only have a global menu.

I tried Gconf but apparently that does not work in 12.10. I then tried Dconf and found this fix on Google: org > gnome > desktop > wm > preferences, look for "button_layout" on the right panel. Here is the problem, after desktop, I do not have 'wm'.

I reset Unity and got a message saying something about wm is missing.

I rebooted and opened Chrome and still no fix. I then clicked maximize and once Chrome was not maximized anymore, the minimize, maximize, close buttons show up in Chrome. Same with Firefox!

Any ideas? I am truly stumped. Firefox and Chrome work fine in KDE Plasma and Gnome when maximized. Sorry for the long post!

---

### Post by chazdg24 on 2012-11-30
Bump.  Anybody...:(

---

