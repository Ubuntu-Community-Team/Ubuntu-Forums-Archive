---
title: "DOSBOX 0.72 Fullscreen &amp; Mouselock Problems"
date: 2009-01-24
forum: Gaming &amp; Leisure
---

### Post by cisforcojo on 2009-01-24
I just installed DOSBOX 0.72 in Ibex and can't go into fullscreen or get mouselock to work. I had it successfully running in Hardy but now it refuses to respond and there's no error output either. Alt-Enter is just like hitting Enter and clicking on the DOSBOX window does nothing.

I've run:
```

CONFIG -writeconf dosbox.conf

```

and re-checked dosbox.conf but no luck! Any ideas???

Compiz is currently disabled.

EDIT: Could this be a problem caused by the commercial ATI driver? I suspect that the driver might not be installed correctly.

---

### Post by cisforcojo on 2009-01-25
Well, I got fullscreen working but the arrow keys refuse to work in the game. I found on [http://www.dosbox.com/](http://www.dosbox.com/) that this is due to Ubuntu 8.10 changing the scancodes for the arrow keys. There's a workaround if you have an American/English keyboard (found at [www.dosbox.com](www.dosbox.com)) but don't attempt it if you're using something else!

NOTE: This fix does not work for me. We'll just have to wait until they patch it.

EDIT 2: The fix works. You have to use the 'keyb xx' command in DOSBox to specify your keyboard layout. For me, it's 'keyb us'

---

