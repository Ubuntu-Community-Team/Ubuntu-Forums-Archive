---
title: "X11 Crashing when using startx and .xinitrc"
date: 2010-06-09
forum: Desktop Environments
---

### Post by jonasg on 2010-06-09
Hello,

I'm using ubuntu to create a HTPC. I don't need a graphical login manager or screen so I removed gdm.
Next I installed ratpoison boxee and zsnes.

My .xinitrc contains 

```

#!/bin/bash
ratpoison &
Boxee &
xbindkeys

```

Using this fails to use 'startx'. It gives me a simple message:

```
ddxsiggiveup
```

The strange thing is when, I enter gnome-session in .xinitrc all works fine ?

Next I've tried using another WM (this time wmii) which gives me another ddxsiggiveup error.

Any clues ?

---

