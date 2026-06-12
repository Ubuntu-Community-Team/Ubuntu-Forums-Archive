---
title: "XModmap doesn't work on Kubuntu"
date: 2005-11-28
forum: Desktop Environments
---

### Post by gnutux on 2005-11-28
Here's a little problem. I usually have the .Xmodmap file to change the Windows key from a key that works like a shift key to an actual key by assigning it F13 or F14.

Yet, KDE doesn't even detect and work for me..

gnutux

---

### Post by ltmon on 2005-11-28
KDE won't look for a .xmodmap file like gnome will.  You need to do a little more work in KDE.

I think (I'm not at my pc now) that I put a link to a script inside my ~/.kde/Autostart directory.

The script would be something like:

```

#!/bin/bash
xmodmap ~/.Xmodmap

```

Make the script exectuable ("chmod +x script.sh") and off you go.

---

