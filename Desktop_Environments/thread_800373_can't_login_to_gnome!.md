---
title: "can't login to gnome!"
date: 2008-05-19
forum: Desktop Environments
---

### Post by lonjim2 on 2008-05-19
I've been running the beautiful Hardy 8.04 for a little while now but am having quite a big problem. I'm able to hit the login screen, but after logging in Ubuntu "freezes". My wallpaper changes colour (w/o loading my desktop background), loads my personalized black cursor and just stops (although I can move the cursor)...

not even sure where to begin.  Thanks for ANY help though!!

---

### Post by gnivler on 2008-05-19
> **lonjim2 said:**
> I've been running the beautiful Hardy 8.04 for a little while now but am having quite a big problem. I'm able to hit the login screen, but after logging in Ubuntu "freezes". My wallpaper changes colour (w/o loading my desktop background), loads my personalized black cursor and just stops (although I can move the cursor)...

not even sure where to begin.  Thanks for ANY help though!!

At the login screen (aka GDM) there is an Options in the bottom left corner, click that, choose Settings, then pick Gnome or Failsafe Gnome and see if you can get in that way.  Sounds like you might have something trying to load which is hanging up and that should bypass it.  You can also try switching VT with ctrl-alt-F1, logging in and checking the logs in /var/log to see if any important errors are being logged.  You can get back to X with ctrl-alt-F7.

---

