---
title: "Stuck with European Input Method"
date: 2008-12-22
forum: General Help
---

### Post by clubsoda on 2008-12-22
To get an inverted comma, I have to type the quote symbol twice, otherwise I end up with umlauts in strange places. Lïkë &#7831;&#7719;ïs.  &#346;á&#7743;é &#7811;íth á&#7765;ò&#347;t&#341;ó&#7765;h&#7869;&#347;, t&#297;ldès and bàc&#7729; qùò&#7831;è&#347;. Bash won´t recognise quote symbols on the command line. :(

This is affecting XFCE only.  I can boot into gnome and the problem goes away.

I´ve reconfigured language settings, completely removed and re-installed SCIM.  The SCIM toolbar won´t show no matter what I do but I don´t think it´s a SCIM problem really.

Help?

[Originally a Gutsy system, upgraded twice.  Standard US-intl keyboard.]

---

### Post by monkeyking on 2008-12-22
does
[PHP]setxkbmap us[/PHP]

make it normal?

---

### Post by clubsoda on 2008-12-22
Yes, thank-you! I wonder why it ever changed...
I found this error in .xsession-errors:-```
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Unable to create /home/clubsoda/.dbus/session-bus
```Looks like that missing file was part of kdebase-bin up until Hardy.

---

