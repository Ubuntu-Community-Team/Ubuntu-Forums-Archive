---
title: "Restting Gnome"
date: 2010-01-28
forum: Desktop Environments
---

### Post by cmnorton on 2010-01-28
I am in a pickle. Today, I just completed rebuilding my workstation. It is Ubuntu 9.10. 

I did load some KDE files, because I want to use Konqueror. 

At the end of the day, I logged out, but needed to log back in right away.

When logging in as the primary user, only an X-term shows at the upper left, and the login won't complete to a fully displayed screen with panels, desktop, and so on. However, my additional users' logins log in with no problems.

For my primary user, what do I need to reset, what files do I need to delete, to get out of this?

I would appreciate any advice or help.

Thank you.

Edit:
------------------------ 
I have tried resetting the .gnome* directories, which did not work. I have a feeling this may be resetting X.

---

### Post by max-power2717 on 2010-01-28
Hi there,

I don't know if this will help, but perhaps simply restarting gdm?

At the login screen press CTRL+ALT+F1, and log into the terminal.

Stop the window manager:
```
sudo /etc/init.d/gdm stop
```Start the window manager:
```
sudo /etc/init.d/gdm start
```You should then be presented with the gnome login screen as per usual.

Hope this solves your issue.

---

### Post by cmnorton on 2010-01-29
Since posting, I have backed up my files; deleted, and then re-created the user with the same problems. I can log in. I get that login screen. But once I log in, I am presented with a tiny little x-term in the upper left.

---

