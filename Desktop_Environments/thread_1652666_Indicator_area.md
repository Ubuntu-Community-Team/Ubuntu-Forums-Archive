---
title: "Indicator area"
date: 2010-12-25
forum: Desktop Environments
---

### Post by Pernig on 2010-12-25
Hi everyone,

Is there any way I can restart the indicator applet (or all the Gnome panels) in the top right corner without logging out and logging back in, or removing it from the panel and putting it back? I find it quite often glitches upon startup and functionality is either partly or wholly lost, necessitating a restart of Gnome.

Sometimes this also happens to the the session indicator too, which makes it difficult to log out or shut down.

Thanks in anticipation.

---

### Post by karthick87 on 2010-12-25
To refresh your panel icons,type the following in your terminal,
```

killall gnome-panel &
```

---

### Post by Frogs Hair on 2010-12-25
System > Preferences > Main Menu > Other , check the box for window manager. this will refresh the entire desktop when the icon is clicked.

I'm not sure why this is happening  and refreshing the desktop is not a long term solution.

---

### Post by Pernig on 2010-12-25
Thanks for these workarounds guys. This is certainly preferable to having to log out and close all my open applications!

> **Frogs Hair said:**
> I'm not sure why this is happening  and refreshing the desktop is not a long term solution.

It sure is irritating. I think I will head over to Launchpad and see if this is a known bug.

---

