---
title: "Resume password"
date: 2008-05-21
forum: Desktop Environments
---

### Post by vies on 2008-05-21
Hi,

Is there a way to get rid off password after resume? 

I have disabled screensaver, changes LOCK_SCREEN=false in /etc/default/acpi-support, but still there is that annoying password.

The reason I want to get it away is that the computer will be mythtv-frontend and suspend/resume works perfectly and system will be on in 5 sec, except that password.

So how to get it away?

---

### Post by sdennie on 2008-05-21
Hit Alt-F2 and type gconf-editor.  Then navigate to /apps/gnome-power-manager/lock and uncheck hibernate and suspend.

---

