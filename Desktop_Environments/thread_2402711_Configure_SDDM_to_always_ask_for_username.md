---
title: "Configure SDDM to always ask for username"
date: 2018-10-03
forum: Desktop Environments
---

### Post by ericjoh on 2018-10-03
Hi,

I have installed Ubuntu 18.04 with SDDM on some machines at work. On all of them I have only one local account (1000:1000) in /etc/passwd since the users are logging in through a central LDAP authentication service. On a few computers it SDDM shows the icon-login-view so that you will have to click on the option to login with another user so that you are able to type in your username. Any idea why those few computers shows the icon-login-view instead of the type-in-username-view?

How can I configure SDDM to always show the type-in-username-view instead of the icon-login-view?

Relevant packages installed:
# dpkg -l|grep sddm
ii  kde-config-sddm                                 4:5.12.6-0ubuntu0.1                         amd64        KCM module for SDDM
ii  sddm                                            0.17.0-1ubuntu7                              amd64        modern display manager for X11
ii  sddm-theme-breeze                               4:5.12.6-0ubuntu0.1                         amd64        Breeze SDDM theme

Best regards / Eric

---

### Post by deadflowr on 2018-10-03
There are themes that are set with username field, where you need type in actual names.
Like this one:
[https://store.kde.org/p/1186478/]("https://store.kde.org/p/1186478/")
and some login themes in general:
[https://store.kde.org/browse/cat/101/]("https://store.kde.org/browse/cat/101/")

just a thought

---

