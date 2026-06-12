---
title: "Compiz suddenly stopped working"
date: 2010-07-24
forum: Desktop Environments
---

### Post by liormk on 2010-07-24
_Hello fellow ubuntuers_

I'm using asus eee pc netbook 1005p with mint 9/gnome (based on ubuntu 10.04) and compiz enabled.
All was well, until a couple of days ago compiz stopped working.
I have no idea what caused it (update? something i've installed?), but i do know it was there and i want it back :) .


Compiz-check gives me the following:
```

    Gathering information about your system...

    Distribution:          Linux Mint 9
    http://www.linuxmint.com/rel_isadora.php
    Desktop environment:   GNOME
    Graphics chip:         Intel Corporation N10 Family Integrated Graphics Controller
    Driver in use:         fbdev
    Rendering method:      AIGLX

    Checking if it's possible to run Compiz on your system...

    Checking for texture_from_pixmap...               [ OK ]
    Checking for non power of two support...          [ OK ]
    Checking for composite extension...               [ OK ]
    Checking for FBConfig...                          [ OK ]
    Checking for hardware/setup problems...           [FAIL]

    There has been (at least) one error detected with your setup:
    Error: Software Rasterizer in use

```


I tried searching for a solution, but only came up with drivers issues, but this netbook does not have an external graphics card, only the onboard one.

Any help would be highly appreciated!

Thanks in advance,
Lior.

---

### Post by liormk on 2010-07-24
SOVLED - I realized that i've changed xorg.conf (for some other problem i had), and that what made the system go for the fbdev driver instead of the intel one.
Once i deleted xorg.conf, all is well again, and compiz-check recognizes that:

Graphics chip:         Intel Corporation N10 Family Integrated Graphics Controller

Sorry for the disturbance :)

---

