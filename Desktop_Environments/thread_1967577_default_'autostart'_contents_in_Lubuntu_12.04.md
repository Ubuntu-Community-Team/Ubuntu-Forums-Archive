---
title: "default 'autostart' contents in Lubuntu 12.04?"
date: 2012-04-28
forum: Desktop Environments
---

### Post by kalehrl on 2012-04-28
Hello

Could somebody post the default contents of 'autostart' file located in /etc/xdg/lxsession/Lubuntu?
I upgraded my Lubuntu this morning and I see that this file was not overwritten.
I want to make sure I have the right file for 12.04.
Thank you

---

### Post by marinara on 2012-04-29
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@xfce4-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

---

### Post by kalehrl on 2012-04-29
Thank you.
I managed to see the default contents with the kind help of Jonathan from lubuntu mailing list.
Basically, run:
[FONT=monospace]
[/FONT]```
[FONT=monospace]dpkg -S /etc/xdg/lxsession/Lubuntu/autostart
```[/FONT]

and you will get lubuntu-default-settings.

Then you can go to [http://packages.ubuntu.com/source/precise/lubuntu-default-settings](http://packages.ubuntu.com/source/precise/lubuntu-default-settings) and either download the archive and open it to see the file or browse Debian Package Source Repository to find the file:
[http://bazaar.launchpad.net/~lubuntu-desktop/+junk/lubuntu-default-settings/view/head:/etc/xdg/lxsession/Lubuntu/autostart](http://bazaar.launchpad.net/~lubuntu-desktop/+junk/lubuntu-default-settings/view/head:/etc/xdg/lxsession/Lubuntu/autostart)

---

