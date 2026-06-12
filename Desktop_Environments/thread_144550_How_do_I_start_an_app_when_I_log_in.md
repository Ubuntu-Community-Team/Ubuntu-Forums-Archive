---
title: "How do I start an app when I log in?"
date: 2006-03-14
forum: Desktop Environments
---

### Post by ardchoille on 2006-03-14
I have been using Window Maker lately and I like it a lot. I found that when I run "gnome-settings-daemon" in Window Maker that my GTK2 apps look really nice.. like they do in gnome. The problem is that I have to manually run gnome-settings-daemon everytime I log into Window Maker. Isn't there a way to make Window Maker run gnome-settings-daemon when it starts? I tried putting
```

gnome-settings-daemon &

```
in both ~/.xinitrc and ~/.xsession but the settings daemon won't ever start that way, I guess those files don't work in Ubuntu 5.10 like they do in other distros. Is there a place I can put the settings daemon so that it will start when Window Maker starts? Could it be that I have the right file (~/.xinitrc or ~/.xsession) but I have the syntax wrong?

---

### Post by Sutekh on 2006-03-14
Try this link?

[Ubuntu Wiki - Custom X Session]("https://wiki.ubuntu.com/CustomXSession")

Its all about the ~/.xinitrc and ~/.xsession.  Check out the last part for a sample ~/.xinitrc

---

### Post by jsvidyad on 2006-03-14
Select System->Preferences->Sessions.

Select the Startup programs tab. Then select Add. Then select command to execute and also the order.

---

### Post by jsvidyad on 2006-03-14
oops. sorry. that works for gnome

---

### Post by ardchoille on 2006-03-15
[QUOTE=Sutekh]Try this link?

[Ubuntu Wiki - Custom X Session]("https://wiki.ubuntu.com/CustomXSession")

Its all about the ~/.xinitrc and ~/.xsession.  Check out the last part for a sample ~/.xinitrc[/QUOTE]
I followed that tutorial two seperte times and it does not work. any other ideas?

---

