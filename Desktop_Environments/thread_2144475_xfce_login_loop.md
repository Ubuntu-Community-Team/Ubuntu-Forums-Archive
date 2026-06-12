---
title: "xfce login loop"
date: 2013-05-12
forum: Desktop Environments
---

### Post by narutoxela on 2013-05-12
Hi everyone, I woke up this morning to notice that my ubuntu 12.10 install with the Xubuntu-desktop environment was in a login loop and I couldn't login. After like 2 hours of fiddling arround I ended up replacing lightdm with lxdm and installing the lubuntu-desktop environment and now it works. The problem is that I still want to use the Xubuntu-desktop environment (xfce) but i still get a login loop when choosing the xfce at the login screen...

Hope this helps (.xsession-errors):

Xsession: X session started for alex at Sun May 12 11:46:13 EDT 2013
localuser:alex being added to access control list
/etc/X11/Xsession: 6: export: Session.mandatory.path: bad variable name

I really want to use xfce, hope someone can help.
Best regards,
Alex


EDIT: I think I found the error (theres no .xsession and .xinitrc), but i dont know how to make new ones...

---

