---
title: "Booting desktop to a specific web page"
date: 2008-08-31
forum: Desktop Environments
---

### Post by Cloudsoft on 2008-08-31
We're trying to set up a computer for a golf club.

We'd like to always boot up into our website.  Ubuntu seems a good choice for security so we'd like to use it.

Can we modify the desktop to always show a specific web page when the computer boots?

The owner of the coffee shop at our (public) course has given us permission to leave the computer there but he'd like to not think about it as much as possible.:)  

Are there any security issues we should be concerned with?

Thanks in advance.

---

### Post by benerivo on 2008-08-31
If you create a new user account and set it to automatically login, then in System > Preferences > Sessions add a new entry with the command```
firefox /http://www.google.com/
```or whatever your site is. Personally i would try Opera, and use its [kiosk mode]("http://www.opera.com/support/mastering/kiosk/"), but i'm sure there will be other suggestions for you.

---

### Post by coolaj86 on 2008-08-31
If you only want that page to be accessible and not other pages, look into prism.

You can also create a desktop that will only have access to the web browser and not other things.

---

### Post by az on 2008-08-31
> **coolaj86 said:**
> If you only want that page to be accessible and not other pages, look into prism.

You can also create a desktop that will only have access to the web browser and not other things.

What about Pessulus?

[I]
lockdown editor for GNOME

pessulus enables the system administrator to set mandatory settings in GConf, which apply to all users, restricting what they can do, which may be of particular usefulness for kiosks (internet cafes, for example).

Examples of what can be locked down are the panels (no changes in the panel configuration are allowed, locking their position and their contents), some of their functions individually (disabling screen locking and log out), the web browser (disabling specific protocols, arbitrary URLs, forcing the user to be in fullscreen mode), among many others.
[/I]

---

