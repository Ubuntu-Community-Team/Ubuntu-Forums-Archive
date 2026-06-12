---
title: "Disable/Remove &quot;Lock Screen&quot; in Gnome Main Menu"
date: 2012-05-10
forum: Desktop Environments
---

### Post by dodle on 2012-05-10
I'm using Ubuntu 10.04 and I have created a "guest" account. I want to remove the "Lock Screen" option from the Main Menu (not the Menu Bar). I've tried changing "/apps/panel/global/disable_lock_screen" in gconf-editor to True, but it is not effected. "/apps/panel/global/disable_log_out" works just fine. I also read [this post](http://superuser.com/questions/62124/how-to-remove-lock-screen-and-logout-from-the-gnome-main-menu-in-sled11), but my system does not have a file called "~/.local/share/gnome-main-menu/system-items.xbel".

---

### Post by vezolmi on 2013-03-27
Hi. You have to change the value of /desktop/gnome/lockdown/disable_lock_screen. Regards

---

