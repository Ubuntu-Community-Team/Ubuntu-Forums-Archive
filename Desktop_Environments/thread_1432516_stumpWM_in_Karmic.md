---
title: "stumpWM in Karmic"
date: 2010-03-17
forum: Desktop Environments
---

### Post by Catalyst2Death on 2010-03-17
Hi,

I'm trying to run stumpwm as my window manager, and I want to run it as its own session (like ion3 or other keyboard driven window managers).

I'm following the instructions here:
[http://ubuntuforums.org/showthread.php?t=577660](http://ubuntuforums.org/showthread.php?t=577660)
and here:
[http://www.xsteve.at/prg/stumpwm/](http://www.xsteve.at/prg/stumpwm/)

To summarize, both say to edit /usr/share/xsessions/stumpwm.desktop
with the following:
```

[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=stumpwm
TryExec=stumpwm
Name=StumpWM
Comment=Stump window manager 

```

I tried this, and other variants (following ion3 as a template) and they all yield the same behavior. *vis. * The session shows up in gdm, I can select it, but when it logs me in X flashes, and then gdm shows up again.  It looks like X11 is crashing, and then gdm restarts.

I've also tried compiling from source and installing.  This works insofar as I can kill metacity and launch stumpwm.  Stumpwm works then, but I can't get it to start X11 with X11 as the primary manager.

I'm aware that there is the option of telling gnome to use stumpwm as the default window manager, but this seems like a bandaid solution.

Also, if anyone has any suggestions for alternative WM let me know.  What I really want is emacs-like keyboard interaction and keybindings.  I know I can get this with ion3, but ion's configuration is LUA, and I really like the fact that stumpwm is written in clisp.

Thanks

---

### Post by Catalyst2Death on 2010-03-18
Friendly bump.

Does anyone know where I can read documentation on making custom GDM sessions for karmic??

---

### Post by Catalyst2Death on 2010-03-21
Hi,

I have another friendly bump... I've got stumpwm working when I do:
```

$ killall metacity; stumpwm &

```
Which gives me what I want, a gnome+stumpwm hybrid desktop that I can use to bridge the gap between just a window manager.

My question now is What is the accepted way of changing the default window manager in gnome? It used to be using gconf (depreciated in 2.12) now it appears that it is either in my .gnomerc:
```

export WINDOW_MANAGER=$HOME/builds/stumpwm/stumpwm/stumpwm

```

But this isn't being respected... (do I need a new line at the end?)
Another method is:
```

$ killall metacity; stumpwm &
$ gnome-session-save # or gnome-session-save --gui

```
Neither of which are respected when I log out and log back in.  Please let me know (or point me to) the right documentation for this issue... Google appears to be useless, but maybe I'm not asking the right questions.

---

### Post by gadzoinks on 2011-12-15
okay, it's 21 months later and i have the same mileage in my Ubuntu 11.04:

sudo apt-get install clisp
sudo apt-get install stumpwm
make the /usr/share/xsessions/stumpwm.desktop file
log out, back in using StumpWM session -- screen blinks, then back to GDM

1) did you ever get this problem figured out, or get an answer?

2) any ideas how i can even diagnose this?

thanks
--jeff

---

