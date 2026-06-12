---
title: "How to find which display manager is currently being used?"
date: 2011-03-09
forum: Desktop Environments
---

### Post by AugustinMa on 2011-03-09
Hello,

How to find which display manager is currently being used? I don't mean desktop environment (KDE, Gnome...) but X11 display manager, like kdm, gdm, ldm, xdm, etc.

See:
[http://en.wikipedia.org/wiki/X_display_manager_(program_type](http://en.wikipedia.org/wiki/X_display_manager_(program_type))

How to switch from one to the other.
I am writing some documentation related to this (because of a problem I recently had) and I'd like more information.

Thanks.

---

### Post by AugustinMa on 2011-03-10
Apparently, nobody knows...

If I every find out, I'll add the information here:
[http://linux.overshoot.tv/wiki/system/desktop_auto_login](http://linux.overshoot.tv/wiki/system/desktop_auto_login) 

Many people ask about the auto-login feature, and many reply, not knowing this actually depends on the display manager. When a non-default is used, that can lead to confusions.

---

### Post by Krytarik on 2011-03-10
...or nobody who knows came across your post, or was willing to answer!

I would bet it is stored there: "/etc/X11/default-display-manager".

At least it says what I am currently using:
```
/usr/sbin/gdm
```
But I don't know for sure if that gets changed when you choose another display manager, since I don't have another one installed.

Greetings.

---

### Post by AugustinMa on 2011-03-20
That's it! Thank you Krytarik.

[http://linux.overshoot.tv/ticket/157#comment-206](http://linux.overshoot.tv/ticket/157#comment-206)

I have updated the article accordingly:
[http://linux.overshoot.tv/wiki/system/desktop_auto_login](http://linux.overshoot.tv/wiki/system/desktop_auto_login)


Blessings,

Augustin.

P.S.
Sorry for the late reply. I am just recovering from a bad cold that knocked me down the whole week.

---

