---
title: "Change GDM fonts?"
date: 2010-05-01
forum: Desktop Environments
---

### Post by Sonybuntu on 2010-05-01
In karmic I was able to open control center by hitting Ctrl+Alt+F1, logging in, and typing in

```
export DISPLAY=:0.0
sudo -u gdm gnome-control-center
```

in a terminal.

Then I hit Ctrl+Alt+F7 and the system hangs up, so now I can't change the fonts that the GDM uses. Is there another way to access the GDM settings? GDM2Setup doesn't really let you change the fonts.

---

### Post by koanhead on 2010-05-01
why not just do 'gnome-control-center' from xterm?

---

### Post by wojox on 2010-05-01
You need Ctrl+Alt+F8

---

### Post by Sonybuntu on 2010-05-01
> **wojox said:**
> You need Ctrl+Alt+F8

Thanks, I guess in Lucid they changed it to F8 instead of F7.

---

### Post by Sonybuntu on 2010-05-03
> **koanhead said:**
> why not just do 'gnome-control-center' from xterm?

I tried that. It doesn't work, launches it in my user, not the GDM.

---

