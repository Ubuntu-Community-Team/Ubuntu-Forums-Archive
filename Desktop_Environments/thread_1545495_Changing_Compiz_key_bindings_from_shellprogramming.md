---
title: "Changing Compiz key bindings from shell/programming language"
date: 2010-08-04
forum: Desktop Environments
---

### Post by imgx64 on 2010-08-04
I found a very annoying bug in compiz (and reported it [here]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/609202").) In short, I need to edit a compiz key binding from gconf-editor every time I reboot the computer because it keeps reverting to its old value.

Until the bug gets fixed, I'm looking for a workaround/kludge. How can I change these settings from the shell or any programming language? I'm thinking of writing a small script/program and run it either manually or automatically (coincidentally, what is the equivalent of .xinitrc in Ubuntu?)

---

### Post by Zorgoth on 2010-08-04
gconftool-2 is the command you are looking for.

---

### Post by Zorgoth on 2010-08-04
Just to be sure, I trust you are using a gconf backend to compiz?

---

### Post by imgx64 on 2010-08-04
Thanks, that's exactly what I needed. This did the trick:

```
gconftool-2 -s /apps/compiz/general/allscreens/options/window_menu_button -t string 'Disabled'
```

:D

---

