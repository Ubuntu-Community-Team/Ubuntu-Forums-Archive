---
title: "Change Icon Size twm"
date: 2019-09-04
forum: Desktop Environments
---

### Post by tomdean@speakeasy.org on 2019-09-04
I use TWM.  Not the Ubuntu desktop.

Every application seems to choose the largest icon when minimized.  Or, maybe this is TWM?

Anyway, the icons are HUGE.  About 3" square.  I want smaller icons.

If I find an application's icon and remove all but 16x16 icon, I get what I want.  Is there a global setting that does this?

---

### Post by him610 on 2019-09-04
Not familar with TWM, but I searched on the term. This webpage turned up, [https://www.x.org/archive/X11R6.8.1/doc/twm.1.html]("https://www.x.org/archive/X11R6.8.1/doc/twm.1.html")
Maybe you can find your answer there.

---

### Post by tomdean@speakeasy.org on 2019-09-06
Thanks, I have read that several times.  I have not found anything that indicates how the icon is chosen when a window is iconized.  Seems like most applications pick the largest icon???
If I delete all the icons except 16x16, iconize still works and I get the desired icon size.

Currently, I remove all the icons except the one I want.  This is a manual operation.  apt restores the removed icons so I have to manually remove them again.

Seems like someone should know how this works.

---

### Post by TheFu on 2019-09-06
> **tomdean@speakeasy.org said:**
>  Seems like someone should know how this works.

Ask the twm project guys.  You are the first person that I've heard of using twm since about 1994.
I would make a script to do what you want, then run it whenever a pixmap icon file looked wrong to me, as needed.

Google found this: [https://lists.fedoraproject.org/pipermail/users/2013-October/442074.html](https://lists.fedoraproject.org/pipermail/users/2013-October/442074.html) which shows .twmrc settings to control the icon used by the *class* of application.
```
    Icons
    {
        "XTerm"    "xterm.icon"
        "xfd"        "xfd_icon"
    }

```

---

### Post by cruzer001 on 2019-09-06
Never tried TWM, I use spectrwm on one install.  Not many people using other WMs these days, the shell rules :)  Why not find a better suited WM?  TheFu runs a nice full featured one from yesteryear.  Mine is lacking features, but does what I want, there are several good ones IMO.

---

