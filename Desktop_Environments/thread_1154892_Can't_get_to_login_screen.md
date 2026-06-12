---
title: "Can't get to login screen"
date: 2009-05-10
forum: Desktop Environments
---

### Post by kooky_LT on 2009-05-10
hello,
 
yesterday I was making some experments with Window server, users, apps and second monitor, and finally my expermentashion finished after restarting, when instead of login screen computer offers me to join host. Any ideas?

---

### Post by Lampi on 2009-05-10
looks like this one is trying to connect to some remote host instead of your localhost machine?

You could check /etc/gdm/gdm.conf from tty terminal - maybe you find some entries in the [servers] section, that don't belong there?

What happens if you hit cancel?
What happens if you stop gdm / restart gdm? (/etc/init.d/gdm restart)

---

### Post by kooky_LT on 2009-05-10
gdm.conf - i think there is some wrong stuff with chooser server...
 
Stop GDM - OK
Start GDM - fail
 
It could be about the driver xsrever-xorg...

---

### Post by kooky_LT on 2009-05-10
any ideas? is there any function to set GDM to default ant does it help?

---

### Post by Lampi on 2009-05-10
If it's a Xorg issue, the LOG files will tell you that!

[list][*]Check /var/log/Xorg.0.log for Xserver related problems[*]Check files in /var/log/gdm for gdm related problems[*]Stop gdm and try to enter Xserver using "startx" from tty terminal[*]Try to rename /etc/gdm.conf and find out what happens if you restart gdm - maybe it'll recreate a new gdm.conf for you that fits all your needs![/list]

---

### Post by kooky_LT on 2009-05-11
I solved it by myself by removing gdm.config-custom
Configuration of GDM servers were incorrect.

---

