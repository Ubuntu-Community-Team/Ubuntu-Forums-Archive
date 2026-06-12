---
title: "Custom keyboard macros in Kile"
date: 2009-02-20
forum: General Help
---

### Post by flogo on 2009-02-20
Hi there,

I am looking for a way to bind certain keystrokes to latex commands (i.e. I would like to press Crtl+AltGr+S to get \sigma and Crtl+AltGr+Shift+S to get \Sigma). Preferably only in Kile. 

I was looking around the Kile options and didn't find anything there. Then I tried xmacroplay together with xbindkeys, but didn't manage to get the macro to play. Is this even the correct approach, or is there an easier solution?

---

### Post by flogo on 2009-02-22
I found a way to do this with xte
```

sleep 0.2
xte 'str \Sigma'

```
but this seems to need the sleep before xte, or it will not always work. The strange thing is that I started the following script from console and it worked fine
```

wmctrl -a kile
xte 'str \Sigma'

```
but when I used a hotkey (settings manager -> keyboard) for it, it only worked in 50% of the cases. When I added the sleep in between the two commands, it always worked.

This seem a bit hackish to me, is there a way to avoid the sleep?

---

### Post by flogo on 2009-02-22
I guess the problem is that I was using Ctrl/Super hotkeys that where still pressed when xte sent the keys, so the keys where modified with Ctrl/Super and did not show.

My next idea would be to use xmodmap and my capslock key, such that

```

capslock + s => \sigma
capslock + Shift + s => \Sigma

```

and so on. I tried this
```

remove Lock = Caps_Lock
keycode 66 = F13
add mod3 = F13

```
But the dialog for Keyboard shortcuts recognized "capslock + s" as "s".
Is it even possible to use a "new" modlevel for shortcuts?

---

