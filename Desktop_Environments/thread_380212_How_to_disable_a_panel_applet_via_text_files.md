---
title: "How to disable a panel applet via text files?"
date: 2007-03-09
forum: Desktop Environments
---

### Post by CaptSaltyJack on 2007-03-09
Gnome has a known issue where mixer_applet2 is running but not visible.  Normally I'd just ignore it, but sometimes it pops up in a tiny window (Beryl does this).  I can't simply remove the applet because it's not visible.  I did a grep for all occurrences of mixer_applet2 in my home folder, I backed up some files and removed mixer_applet2 from them.. the damn thing STILL loads up when I log in!!

How do I temporarily get rid of this thing until this bug is (hopefully?) fixed in Feisty?

---

### Post by Joshua Swink on 2007-12-11
Make sure that the relevant file in /etc/xdg/autostart contains "X-GNOME-Autostart-enabled=false".

echo X-GNOME-Autostart-enabled=false >> /etc/xdg/autostart/NAME.desktop

For example:

echo X-GNOME-Autostart-enabled=false >> /etc/xdg/autostart/mixer_applet2.desktop

Related documentation: [http://standards.freedesktop.org/autostart-spec/autostart-spec-0.5.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-0.5.html)

---

