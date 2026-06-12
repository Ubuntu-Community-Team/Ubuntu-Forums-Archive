---
title: "xmodmap weirdness / laggy / unreliable"
date: 2009-03-08
forum: General Help
---

### Post by sototallycarl on 2009-03-08
A super problematic issue is happening with my xmodmap config when I am swapping the ctrl and alt keys. often the alt key with act as both the alt and ctrl key and say i am hitting delete at the same time, BAM, there goes my current x session and anything I was working on.

Is this common? Maybe I am doing it wrong?

Here is what I am using:
```

remove Control = Control_L Control_R
remove Mod1    = Alt_L Alt_R
add    Control = Alt_L Alt_R
add    Mod1    = Control_L Control_R

```

---

### Post by cubeist on 2009-03-08
Two things.. first, then naming of the xmodmap file is case sensitive... this would be the simple fix...
```
.Xmodmap
```

If that is ok, I would just use keycodes to change what you want...so open a terminal, run xev, jot down the keycodes for alt L&R and Ctrl L&R and then specifically name the keys in this format:
```
keycode ## = Alt_L
```

---

