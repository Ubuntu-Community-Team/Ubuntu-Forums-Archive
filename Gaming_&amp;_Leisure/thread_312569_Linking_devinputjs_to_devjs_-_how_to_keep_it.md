---
title: "Linking /dev/input/js to /dev/js - how to keep it?"
date: 2006-12-04
forum: Gaming &amp; Leisure
---

### Post by Saubazi on 2006-12-04
I noticed that in some cases wine is looking for /dev/js0 and not able
to find a joystick device from /dev/input/js0 - solution make a softlink to the device node under /dev. Now it disappears after a reboot - how can I make it permanent?

---

### Post by tagra123 on 2006-12-12
> **Saubazi said:**
> I noticed that in some cases wine is looking for /dev/js0 and not able
to find a joystick device from /dev/input/js0 - solution make a softlink to the device node under /dev. Now it disappears after a reboot - how can I make it permanent?



Using the Menu: Applications-Accessories-Terminal

Type
```

sudo gedit /etc/udev/rules.d/60-symlinks.rules
```

Place the following at the bottom of the file:

```
# Create Joystick /dev/js0, /dev/js1, etc using symlink 
#(links /dev/input/jsX to /dev/jsX)
KERNEL=="js[0-9]*", SYMLINK+="%k"
```

save the file and exit.

On reboot the joystick can be found by the programs looking for /dev/js0 as well as /dev/input/js0

---

### Post by RFXCasey on 2008-10-01
> **tagra123 said:**
> Using the Menu: Applications-Accessories-Terminal

Type
```

sudo gedit /etc/udev/rules.d/60-symlinks.rules
```

Place the following at the bottom of the file:

```
# Create Joystick /dev/js0, /dev/js1, etc using symlink 
#(links /dev/input/jsX to /dev/jsX)
KERNEL=="js[0-9]*", SYMLINK+="%k"
```

save the file and exit.

On reboot the joystick can be found by the programs looking for /dev/js0 as well as /dev/input/js0


When it says KERNEL=="js[0-9]*", SYMLINK+="%k"[/CODE] does 0-9 mean pick a number 0 through 9 or is that code supposed to be literal?

---

