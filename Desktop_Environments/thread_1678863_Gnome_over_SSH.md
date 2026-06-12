---
title: "Gnome over SSH"
date: 2011-01-31
forum: Desktop Environments
---

### Post by Gaku on 2011-01-31
Hello!

How I can get access to my Gnome Desktop through PuTTY?

---

### Post by nothingspecial on 2011-01-31
You need to forward X

```
ssh -X user@host
```

Then type ```
gnome-panel
``` and you can clickety click what ever you like.

---

### Post by Gaku on 2011-01-31
I'm using PuTTY. After log-in, typeing gnome-panel and seeing:

> (gnome-panel:1211): Gtk-WARNING **: cannot open display: localhost:10.0
ubuntu@domU-12-31-39-10-60-9D:~$ gnome-panel

(gnome-panel:1212): Gtk-WARNING **: cannot open display: localhost:10.0


What does it mean?

---

