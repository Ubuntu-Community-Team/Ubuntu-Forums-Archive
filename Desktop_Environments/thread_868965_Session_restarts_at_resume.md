---
title: "Session restarts at resume"
date: 2008-07-24
forum: Desktop Environments
---

### Post by theophile on 2008-07-24
Using latest Hardy.

When I resume my system from suspend, I have to log in via GDM, the previously running GNOME session is lost, and it is as though I am booting fresh every time.

LOCK_SCREEN is already commented out in /etc/default/acpi-support and it makes me login again anew anyway.

How can I prevent this from happening?

---

### Post by sola on 2009-08-18
I have the exact same problem with Jaunty on a Toshiba m200 laptop (with nvidia fx 5200 go graphics).

This happens sometimes but not always. Very annoying. 

It seems that it doesn't happen when there is no external monitor attached.

This is very likely due to the X Server crashing at resume.

---

