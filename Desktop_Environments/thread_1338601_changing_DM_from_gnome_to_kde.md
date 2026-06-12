---
title: "changing DM from gnome to kde"
date: 2009-11-26
forum: Desktop Environments
---

### Post by andreyvul on 2009-11-26
I installed ubuntustudio and the default DM changed from KDE to GNOME. How do I change the system DM (back) to KDE?

Note: I'm runnning X via startx instead of kdm.

---

### Post by bmorency on 2009-11-27
> **andreyvul said:**
> I installed ubuntustudio and the default DM changed from KDE to GNOME. How do I change the system DM (back) to KDE?

Note: I'm runnning X via startx instead of kdm.


in the console  type this:

```
more /etc/X11/default-display-manager
```

What comes up for you? I have:

 /usr/bin/kdm

If you don't have that try to change it and see what happens.

---

### Post by andreyvul on 2009-11-28
Yes, cat /etc/X11/default-display-manager outputs /usr/bin/kdm, but the root cause has something do do with Xsession options.
Now, I'm looking over /etc/X11/Xsession.options to see where it imports the WM envvar or whatever it uses from.

---

### Post by bmorency on 2009-11-28
I found this site. it may help you out.

[http://www.tuxfiles.org/linuxhelp/changeman.html]("http://www.tuxfiles.org/linuxhelp/changeman.html")

---

