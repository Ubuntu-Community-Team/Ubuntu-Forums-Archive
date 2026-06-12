---
title: "Can't change from default gnome icon theme?"
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by trent1978 on 2007-07-28
Hi Guys/Gals,

I've been running Fiesty for a few weeks now on my desktop PC, AMD64.. i'm running the 32bit version of Fiesty though... anyway for some reason, i can't change the icon theme from the default. I've tried installing theme's as per many instructions found on these forums (thanks). I've even tried to change to one of the other pre-installed icon sets but nothing changes - that said if i go back into the theme, the icon set is listed as being changed...

Anyone got any idea's or had this problem before?

Thanks in advance..

Trent. :confused:

---

### Post by Lapeth on 2007-10-10
Do you run Compiz Fusion?

I have the same problem when xgl + compiz is loaded, but running a session with the regular metacity (and no xgl) enables me to change the icon theme. When I load back into xgl + compiz, the icons are back to the "GNOME" theme.

---

### Post by Forlong on 2007-10-10
If you're on Xgl, try running this:
```
gnome-settings-daemon
```

---

### Post by Lapeth on 2007-10-24
Well, that seems to do the trick. Thanks.

Only problem now is that it takes quite a long time to run, which doesn't make it fun to run in startup.

---

