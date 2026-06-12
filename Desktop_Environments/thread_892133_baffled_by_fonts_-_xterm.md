---
title: "baffled by fonts - xterm"
date: 2008-08-16
forum: Desktop Environments
---

### Post by ktenney on 2008-08-16
Howdy,

I've been trying to figure out how fonts are managed for xterm.
As a result of lots of attempts which I no longer recall, 
starting xterm reports
xterm:  unable to open font "verdana", trying "fixed"....

There was a time I could start xterm with the font size I desired using
xterm -fa rk -fs 18

It was good then, now I only see courier ~10

Where is xterm getting instructions to use verdana?

How can I revert to pre mucked up?

Thanks,
Kent

---

### Post by RedSquirrel on 2008-08-16
Do you have an old .Xdefaults or .Xresources file lying around in your home directory? If so, perhaps there is a setting for Verdana in there.

```
xterm -fa rk -fs 18
```

That is correct, as long as you have the font installed, e.g.,

```
xterm -fa Monospace -fs 12
```

---

### Post by bingoUV on 2008-08-17
Figure out the fonts available to you:
```

xlsfonts

```

Use any of these in xterm e.g. -adobe-courier-medium-o-normal--25-180-100-100-m-150-iso10646-1
```

xterm -fn '-adobe-courier-medium-o-normal--25-180-100-100-m-150-iso10646-1'

```

---

### Post by ktenney on 2008-08-17
> **RedSquirrel said:**
> Do you have an old .Xdefaults or .Xresources file lying around in your home directory? If so, perhaps there is a setting for Verdana in there.

```
xterm -fa rk -fs 18
```

That is correct, as long as you have the font installed, e.g.,

```
xterm -fa Monospace -fs 12
```

Well, this AM it's ok. I had deleted ~/.Xresources, possibly needed
to restart X ... ?

Just wondering, where do I learn about things like the relation between
"rk" and "Monospace" in the 2 command lines above?

Thanks,
Kent

---

