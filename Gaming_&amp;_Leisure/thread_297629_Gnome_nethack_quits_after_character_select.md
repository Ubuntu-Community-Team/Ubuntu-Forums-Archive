---
title: "Gnome nethack quits after character select"
date: 2006-11-11
forum: Gaming &amp; Leisure
---

### Post by Peepsalot on 2006-11-11
EDIT: [nevermind](https://launchpad.net/distros/ubuntu/+source/nethack/+bug/55563)

---

### Post by apocralypse on 2006-11-15
Haha, I have the same problem. Can you (or someone else) explain the "never mind". I'm guessing I'm missing something obvious : )

Cheers

-Kev-

---

### Post by Peepsalot on 2006-11-15
> **apocralypse said:**
> Haha, I have the same problem. Can you (or someone else) explain the "never mind". I'm guessing I'm missing something obvious : )

Cheers

-Kev-
I made that word a link.  if you follow the link, there is a fix at the end:
run this in terminal
```

export XLIB_SKIP_ARGB_VISUALS=1

```
then you can start nethack with "nethack-gnome"

Alternatively you can save the following to a script file.  I made mine as usr/bin/nethack
```

#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
nethack-gnome

```
Don't forget to do
```

sudo chmod +x script_name

```
to make the script executable.

---

### Post by Wolfan on 2008-03-08
Thanks very much Peepsalot

---

