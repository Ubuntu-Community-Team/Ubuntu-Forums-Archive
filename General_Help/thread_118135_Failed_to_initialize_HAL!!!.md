---
title: "Failed to initialize HAL!!!"
date: 2006-01-16
forum: General Help
---

### Post by serioussam909 on 2006-01-16
When I tried to start Ubuntu normally, then at "starting kernel log daemons" it shows [failed] and after that there is blank screen.
I tried to enter safe mode , & typed startx, then it shows "Failed to initialize HAL!!!".
X window system works, but only in safe mode.
What's wrong?

---

### Post by dcstar on 2006-01-16
[QUOTE=serioussam909]When I tried to start Ubuntu normally, then at "starting kernel log daemons" it shows [failed] and after that there is blank screen.
I tried to enter safe mode , & typed startx, then it shows "Failed to initialize HAL!!!".
X window system works, but only in safe mode.
What's wrong?[/QUOTE]
Edit /etc/default/bootlogd to have:

BOOTLOGD_ENABLE=Yes

Edit /etc/default/rcS to have:

VERBOSE=yes

Then after a reboot look at the /var/log/boot log file for any error messages about what failed.

You may be able to identify and repair the particular section, but it may need a re-install if it is too far gone.

---

### Post by seekyrr on 2006-02-24
I just started having a HAL error my self.  Wont load gnome and puts me at a command prompt login.  If I startX it loads gnome but no apps work.

It seems to fail on Gnome start and fails on Deferred execution scheduler.  Also it appears to Fail to bring up eth1.

I dont want to loose all my work so far.  Any help would be appreciated.

Seeky

EDIT.

I want to try sudo apt-get install --reinstall hal   but I can't get the networking interface to come up.

How can I install that from CD?

Thanks

---

