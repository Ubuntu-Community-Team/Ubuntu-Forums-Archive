---
title: "Gnome Gmail Notifier and Ubuntu 12.10 Quantal Quetzal"
date: 2012-10-22
forum: Desktop Environments
---

### Post by kiaeix on 2012-10-22
I use Gnome Classic instead of Unity. Since I've done the crapdate from 12.04 to 12.10 the whole message indication is malicious. I have no mail icon from the "indicator-massages" package in order to use for example "gm-notify". After installing "gnome-gmail-notifier" and starting it, it just stucks. Anyone any idea?

---

### Post by markbl on 2013-01-02
FYI, I just updated my [gmail-indicator](https://github.com/bulletmark/gmail-indicator) for Ubuntu 12.10.

I created the simple and light-weight gmail-indicator because gm-notify did not work for gnome-shell (at least back when I used it). Like gm-notify, gmail-indicator uses push from the server unlike most other notifiers which simply poll periodically. Gmail-indicator integrates into the Ubuntu messaging menu on Unity etc, and into the gnome panel on Gnome-shell.

---

