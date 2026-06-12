---
title: "Gnome shell panel changes size and windows look gtk1 like"
date: 2011-03-26
forum: Desktop Environments
---

### Post by christooss on 2011-03-26
I have installed Gnome Shell through Gnome team ppa [https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3) and it installs fine (I think) I have installed gnome-shell and than updated my 11.04 system.

Now I have two problems. 
1.) Window borders (ie theme are looking really old gtk1.0 like probably just some default themem) and icon theme is missing. I tried changing theme in gconf-editor desktop/gnome/shell/windows. I used Ambiance but it doesn't seem to work. Changing close and maximize buttons work wp.

It seems that gnome-session-manager is crashing
2.) Panel size changes. From huge (when apps are shown) and normal when Activities are open.

Some settings I found in gnome-shell.css

```
.app-menu-icon {
    width: 24px;
    height: 24px;
}
```

And settings from js/ui/panel.css

```
const PANEL_ICON_SIZE = 24;
```

It seems these settings are default. Thing is panel is 24px only when Activities are active (look at both screenshots)

I hope i got this in right forum. I really hope you have some ideas about my problems. Tnx for the anwsers.

---

