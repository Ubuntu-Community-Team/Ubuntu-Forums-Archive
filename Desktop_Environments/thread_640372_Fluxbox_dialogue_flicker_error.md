---
title: "Fluxbox dialogue flicker error"
date: 2007-12-14
forum: Desktop Environments
---

### Post by Dixon Bainbridge on 2007-12-14
Having a strange problem in Fluxbox - whenever I get a save dialogue box come up in any app, it goes mad - rapid resizing flickering thing. The only app immune to it so far is Opera.

Browse to other folders option stops it. I think its a GTK error. Anyone know how to fix it?

I'm on Feisty.

Thanks.

---

### Post by RedSquirrel on 2007-12-14
That's a GTK bug. It's not present in the version of GTK on gutsy. The only ways to fix it that I know of are to click "Browse for other folders" or to upgrade to gutsy. ;)


Edit:

I also used the following line in my ~/.fluxbox/keys file to make the "Save As" dialog a little larger by pressing Ctrl-Alt-s. This didn't work all the time, though. You can also press Alt and right-click your mouse to resize the dialog.

```
Control Mod1 s  :ResizeTo 800 600
```

---

### Post by Dixon Bainbridge on 2007-12-15
Hey, thanks for that man. I thought it was a bug... I might well upgrade to gutsy soon anyway.

---

