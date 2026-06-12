---
title: "Arrow keys disabling, odd Unity notification icon"
date: 2015-07-08
forum: Desktop Environments
---

### Post by mattgyver83 on 2015-07-08
Hey guys, I am running 15.04 with Unity and for some reason recently when scrolling using the arrow keys somewhat fast they stop working, a reboot always fixes this but gosh its annoying.  When it happens the only direction that works is the left arrow and I get an icon that displays in the notification area that looks like the touchpad with an X on it however the touchpad is not disabled and works fine.

Does anyone have any idea on what that could be or any leads on what to check into?  Thanks its really annoying!

---

### Post by mattgyver83 on 2015-07-08
Not sure if this is a long term fix but digging through some other forum posts I found running;

sudo dpkg-reconfigure keyboard-configuration

And selecting "Acer Laptop" (As I have an Acer) should correct the default settings.  I am guessing that maybe the last dist-upgrade I did a while back set me as something else like a empty value or default but I failed to check /etc/default/keyboard prior to running dpkg-reconfigure so (hopefully) I'll never know.

---

