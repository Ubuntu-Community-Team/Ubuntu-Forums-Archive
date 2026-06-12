---
title: "Maximum Clients reached, Zenity notifications"
date: 2011-11-18
forum: Desktop Environments
---

### Post by npluis on 2011-11-18
Hi,

Ever since upgrading to 11.10 I get the `Maximum number of clients reached` message when starting a new application. 

```
xlsclients
```shows a lot of zenity clients (currently 173). 

```
ps aux | grep zenity
```Shows (also 173) lines like this:
10528  0.0  0.1  77880 11096 ?        Sl   Nov17   0:00 /usr/bin/zenity --notification --window-icon /usr/share/icons/gnome/32x32/status/mail-unread.png --text You have new mail

How can I stop this from happening?

---

