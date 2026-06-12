---
title: "KDE4 Panel is Gone"
date: 2008-01-12
forum: Desktop Environments
---

### Post by JustinAlf on 2008-01-12
I restarted my computer with KDE4 and everything was fine and great.  But I restarted a second time, and my Panel was gone.  What is the command for the KDE4 Panel!?  Please help.  I"m runing Kubuntu Gutsy with KDE4.

---

### Post by tolstolobik on 2008-01-12
Almost the same. Kubuntu 7.10

---

### Post by GeneralZod on 2008-01-12
[http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Where_has_my_panel_disappeared_to.3F.21](http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Where_has_my_panel_disappeared_to.3F.21)

---

### Post by tolstolobik on 2008-01-12
Thx man, that was quick :)

---

### Post by JustinAlf on 2008-01-12
Thanks for the Help!

---

### Post by lamerlamer on 2008-04-09
Please post solution here
[http://techbase.kde.org/index.php?title=Projects/Plasma/FAQ#My_panel_is_gone.2C_how_do_I_get_it_back.3F](http://techbase.kde.org/index.php?title=Projects/Plasma/FAQ#My_panel_is_gone.2C_how_do_I_get_it_back.3F) Does not work :(

---

### Post by lamerlamer on 2008-04-10
**Solution:**
> **My panel is gone, how do I get it back?**
kquitapp plasma; rm $KDEHOME/share/config/plasma-appletsrc; plasma

This deletes your plasma settings, so you'll get the default configuration back. The panel-vanishing-on-crash issue was fixed just after 4.0.0's release. If running all the 3 commands at once doesn't work, try typing them in manually and wait a few seconds before running the next command.
=D>

---

### Post by justgeig on 2008-04-23
Ok so this seems to be the only solution for the disappearing panel but it doesnt work for me...any other solutions?

---

### Post by rryan on 2008-04-23
I tried the fix in the Kubuntu 8.04 release candidate and it doesn't work because $KDEHOME is not defined by default. It should point to /home/$USER/.kde4/. For those that are having trouble, try this:

```
kquitapp plasma; rm /home/$USER/.kde4/share/config/plasma-appletsrc; plasma
```

---

### Post by justgeig on 2008-04-23
that did the trick thanks a bunch!

---

