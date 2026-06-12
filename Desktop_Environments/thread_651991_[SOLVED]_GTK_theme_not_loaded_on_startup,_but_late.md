---
title: "[SOLVED] GTK theme not loaded on startup, but later (or tiny fonts)"
date: 2007-12-28
forum: Desktop Environments
---

### Post by kowey on 2007-12-28
Here are my symptoms.  When I first log in, I get an old theme with really tiny fonts (see [before screenshot]("http://bp2.blogger.com/_c6WmXt2id8U/R3TNAPXYD8I/AAAAAAAAAGM/qfFvc6RtzE4/s1600-h/font-weirdness-before.png")), but once I run certain applications, particularly rhythmbox, my other GTK-using applications start using the fancy Ubuntu theme, notably with regular sized fonts (see [after screenshot]("http://bp1.blogger.com/_c6WmXt2id8U/R3TNG_XYD9I/AAAAAAAAAGU/uRpypvMY2m8/s1600-h/font-weirdness-after.png")).

Anybody know what's up?  This kind of irregularity makes gvim a pain to use, because you can't just pick one font size.  The workaround so far is just to start rhythmbox first thing, but eh...

Also, I'm using xmonad as a window manager, and my .xsession loks like this:
```

xmodmap ${HOME}/custom/keyboard/dvorak_nc_accent.xmm
xterm &
PIPE=${HOME}/.xmonad.log
mkfifo -m 600 ${PIPE}
[ -p ${PIPE} ] || exit
xmobar &
/usr/local/bin/xmonad > ${PIPE}
```

---

### Post by kowey on 2008-01-29
I just needed to put
```
gnome-settings-manager &
```
in my .xsession

---

