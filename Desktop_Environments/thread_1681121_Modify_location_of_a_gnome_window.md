---
title: "Modify location of a gnome window"
date: 2011-02-03
forum: Desktop Environments
---

### Post by gamblor01 on 2011-02-03
Does anyone know if it's possible to specify a screen location when opening a window in gnome?  I have created a custom launcher on the top panel in gnome.  It launches a bash script that I wrote, but the script requires input that can change.  The launcher command is like this:

```

gnome-terminal -x bash -c "buildit"

```The functionality of it works great.  What I would like to do however, is control where the gnome-terminal window actually opens.  It seems be random and based on other windows that are open.  So sometimes it opens on the top-left of the screen, other times it's the bottom-left, etc.  I use Compiz as my window manager (e.g. under System > Preferences > Appearance > Visual Effects I have chosen the "Normal") with an Nvidia 8600GT (driver version is 260.19.06).

Is there some way I can control the screen location (maybe specify the x,y coordinate) of where I want this window to open?  Ideally it would be great to force the window to open directly below the icon in my panel.  Is this even possible?

---

### Post by gamblor01 on 2011-02-03
Nevermind...I finally did a search for "gnome-terminal geometry position" on google and found the answer here:

[http://superuser.com/questions/72176/linux-set-default-terminal-size-and-screen-position](http://superuser.com/questions/72176/linux-set-default-terminal-size-and-screen-position)

Essentially you can just pass a --geometry option to gnome-terminal.  So I just changed my launcher to do:

```

gnome-terminal --geometry=80x24+1100+0 -x bash -c "buildit"

```


This opens a gnome-terminal window that is 80 characters by 24 lines at position x=1100,y=0.  It works perfectly!

---

### Post by chox_de on 2011-10-16
Another, more general approach would be to use the program "wmctrl" from the universe repository.
It can be used to place / move / resize / etc. ANY windows that are managed by the Window Managers listed here: [http://tomas.styblo.name/wmctrl/](http://tomas.styblo.name/wmctrl/)
If you don't want to read - the standard window managers for KDE and GNOME are amongst them, thus working for Ubuntu (tried under 11.10), Kubuntu, etc. ;)

Just for the times when compiz-plugin for window placement won't do...

---

