---
title: "Why have colors suddenly become dark and saturated in Gtk3 features &amp; applications?"
date: 2017-10-15
forum: Desktop Environments
---

### Post by jaywad on 2017-10-15
I've tried to search through the forums to find out why my folder/files icons became darker, why my font is different than how it was before and why many system applications are very saturated in color (nautilus, terminal, document viewer etc.). I've tested many workarounds without luck.


**The pattern I see here is that GNOME applications are affected and all applications that relies on GTK3 since I am using the adapta-gtk-theme, though I'm not sure if this is related in any way.**


I am using Lenovo thinkpad T460s with Ubuntu 16.04 running with GNOME desktop environment and having Lenovo Skyland integrated graphic card (Intel driver).


How can I fix this?

Before:
[IMG]https://i.stack.imgur.com/gTT8b.png[/IMG]

After:
[IMG]https://i.stack.imgur.com/zh5DU.png[/IMG]

---

### Post by again? on 2017-10-15
Create and test a new user account.

---

### Post by jaywad on 2017-10-18
[COLOR=#111111][FONT=Ubuntu]My problem was solved with a full-upgrade today. Some mesa related libraries, adapta-gtk-theme and xserver-xorg-core were updated with some additional libraries.[/FONT][/COLOR]

---

### Post by jaywad on 2017-10-18
I created a new user as a test user recently and same issue was happening.

---

### Post by jaywad on 2017-10-18
> **guber2 said:**
> Create and test a new user account.

I created a new user as a test user recently and same issue was happening.

---

