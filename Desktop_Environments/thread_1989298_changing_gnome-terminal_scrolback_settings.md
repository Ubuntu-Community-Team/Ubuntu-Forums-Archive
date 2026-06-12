---
title: "changing gnome-terminal scrolback settings"
date: 2012-05-28
forum: Desktop Environments
---

### Post by piriton on 2012-05-28
How can I configure and increase the gnome-terminal scrollback settings using an automated tool ?  Yes I could just select a few options in the menu using the mouse but I would like to learn something more.

Can gsettings do this ?  So far i've not been able to figure out how.

---

### Post by drs305 on 2012-05-28
Are you looking to change the number of scrollback lines available? That's changed via Edit > Profile Preferences > Scrolling.

If that isn't what you are looking for, by automated tool, do you mean a GUI app?

I didn't find a scrollback setting in dconf for gnome-terminal. There is still a setting in gconf-editor in /apps/gnome-terminal/profiles/Default/scrollback_lines, so it could be changed via a terminal command if desired.

---

### Post by piriton on 2012-05-28
>Are you looking to change the number of scrollback lines available?

Yes, I would like to do this using a configuration tool or by editing a config file to set this value.

---

### Post by drs305 on 2012-05-28
> **piriton said:**
> >Are you looking to change the number of scrollback lines available?

Yes, I would like to do this using a configuration tool or by editing a config file to set this value.

gconf-editor is the GUI app, but as I mentioned you can also just do it via the gnome-terminal preferences as well.
```
gconf-editor /apps/gnome-terminal/profiles/Default
```

---

### Post by piriton on 2012-05-28
```

gconftool-2 -t int --set /apps/gnome-terminal/profiles/Default/scrollback_lines 10000
```

Cool, thanks a lot !

---

