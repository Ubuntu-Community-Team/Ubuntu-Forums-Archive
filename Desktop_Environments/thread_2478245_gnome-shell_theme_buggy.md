---
title: "gnome-shell theme buggy"
date: 2022-08-20
forum: Desktop Environments
---

### Post by speedrunnerG55 on 2022-08-20
OS: Ubuntu 22.04.1 LTS x86_64
GNOME Shell 42.2
XOrg 1.21.1.3 (12101003)

I believe something has modified my gnome-shell-theme.gresource 

 I've tried reinstalling gnome-shell-common but that did not change my problem.

[https://imgur.com/a/i6R2hPC](https://imgur.com/a/i6R2hPC)

The activities menu is really buggy and hard to use

---

### Post by Claus7 on 2022-08-21
Hello,

this will change your configurations, yet it will reset your system to defaults:
1) dconf reset -f /org/gnome/
2) gnome tweaks->sandwich icon->reset to defaults

link: [https://ostechnix.com/reset-gnome-desktop-settings-to-default-in-linux/](https://ostechnix.com/reset-gnome-desktop-settings-to-default-in-linux/)

haven't tested them though.

Regards!

---

