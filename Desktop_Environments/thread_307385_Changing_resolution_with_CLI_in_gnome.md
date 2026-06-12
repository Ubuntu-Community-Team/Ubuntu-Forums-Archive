---
title: "Changing resolution with CLI in gnome"
date: 2006-11-26
forum: Desktop Environments
---

### Post by kaamos on 2006-11-26
Hello!

I have a laptop that has a fn+FX key for swapping between an external monitor and the lcd of the laptop. This does not work in ubuntu (or any other distro for that matter), so I'm using a script that is bind to a key kombination. This is working fine except that very few monitors support the native resolution of the laptop (1400x1050) and I haven't found a way to add the resolution change to the script.

```
gconftool-2 -s /desktop/gnome/screen/default/0/resolution --type=string 1024x768
```

This sets the gconf key, but it's not enough to make X change the resolution. Any ideas on this?

Btw. here is the script that I'm using in case someone else finds it useful.

EDIT: Ok, got it. Using xrandr seems to work.

```

#!/bin/bash

crt_present=$(aticonfig --query-monitor|grep Connected|grep crt1|wc -l)

if [ $crt_present == 0 ]; then
    echo "crt not connected!"
    exit 1;
fi

crt_state=$(aticonfig --query-monitor|grep Enabled|grep crt1|wc -l)

if [ $crt_state == 1 ]; then
    echo "crt is on, switching xv"
    aticonfig --enable-monitor=lvds >/dev/null 2>/dev/null
    xrandr -s 0
else
    echo "crt is off, enabling"
    xrandr -s 1
    sleep 1
    aticonfig --enable-monitor=crt1 >/dev/null 2>/dev/null
fi


```

---

