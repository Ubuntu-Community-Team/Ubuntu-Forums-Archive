---
title: "Use Open Box with xfce"
date: 2009-03-27
forum: Desktop Environments
---

### Post by kut77less on 2009-03-27
How  would I do this?

---

### Post by kerry_s on 2009-03-27
in your openbox start up put the parts you want.
example:

panel = xfce4-panel &
desktop= xfdestop &

thats pretty much all you need from xfce4. i only use Thunar on my jwm setup.

wait, just remembered i use orage and squeeze to, orage i have set on my clock click, and squeeze through the thunar plugin. :)

---

### Post by kut77less on 2009-03-27
> **kerry_s said:**
> in your openbox start up put the parts you want.
example:

panel = xfce4-panel &
desktop= xfdestop &

thats pretty much all you need from xfce4. i only use Thunar on my jwm setup.

wait, just remembered i use orage and squeeze to, orage i have set on my clock click, and squeeze through the thunar plugin. :)



Were would I past this. Sorry I have no Idea I am kinda new to linux. Thanks

---

### Post by Denestria on 2009-03-27
Edit or create the file *.config/openbox/autostart.sh*
This where you add the programs you want openbox to start on login like the panel.

```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup
thunar --daemon & (for handling removable media)
update-notifier &

# Programs that will run after Openbox has started
xfce4-panel &
pidgin &

```

---

### Post by kerry_s on 2009-03-27
according to the man pages it's> ~/.config/openbox/autostart.sh
so 
press alt+f2 or in terminal
type> mousepad ~/.config/openbox/autostart.sh

from thunar, press ctrl+h , to see hidden folders/files
click> .config > openbox > autostart.sh

are you in openbox? (log out of xfce4, select openbox in the menu, log in)

---

### Post by kut77less on 2009-03-27
> **Denestria said:**
> Edit or create the file *.config/openbox/autostart.sh*
This where you add the programs you want openbox to start on login like the panel.

```
# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup
thunar --daemon & (for handling removable media)
update-notifier &

# Programs that will run after Openbox has started
xfce4-panel &
pidgin &

```




Hey is there a way to start up compiz fusion? 

Thanks for your help

---

### Post by kerry_s on 2009-03-27
compiz fusion is a window manager, openbox is a window manager
you can only have 1 window manager running.

---

