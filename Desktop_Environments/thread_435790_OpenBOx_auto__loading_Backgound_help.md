---
title: "OpenBOx auto  loading Backgound help?"
date: 2007-05-07
forum: Desktop Environments
---

### Post by mazingaz on 2007-05-07
I have installed 7.04 server with Openbox Wm and it works and all but when I tried to to execute autoload of background image using feh and pypanel  it always loads openbox default screen(grey screen). 

I do not use any xsession (XDM. GMD KDM) so I figured configuring ~/.xinitrc would do but it is not working I even tried configuring /etc/xinit/xinitrc file but that didn't work either.

This is what my ~/.xinitrc looks like

```

exec openbox
pypanel &
conky &
eval `cat $HOME/.fehbg` &

```

Also i have noticed

After installing xorg then openbox, executing startx would start the openbox without having to configuring ~/.xinitrc or the /etc/xinit/xinitrc.  Where does ubuntu search for the WM execution command?

---

### Post by mazingaz on 2007-05-07
NE One?

---

### Post by EndPerform on 2007-05-07
You need to put exec openbox as the last line in your .xinitrc.  Below is mine:

```
gnome-settings-daemon &
gnome-volume-manager &
eval `cat $HOME/.fehbg` &
conky &
perlpanel &
exec openbox
```

Basically, anything I want to load with openbox needs to go before actually executing openbox itself, which is why you are seeing the defaults.

---

### Post by mazingaz on 2007-05-09
Got it~
Thanks

---

### Post by mazingaz on 2007-05-09
Got it~
Thanks

---

