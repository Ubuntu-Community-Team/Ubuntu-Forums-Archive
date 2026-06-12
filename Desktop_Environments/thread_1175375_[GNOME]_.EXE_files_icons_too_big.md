---
title: "[GNOME] .EXE files icons too big"
date: 2009-06-01
forum: Desktop Environments
---

### Post by carlosgs91 on 2009-06-01
.

---

### Post by ckonestroh on 2009-06-01
Whats with all these files on your desktop.....

Thats why we have cairo / gnome do ....

What a mess...

This not a windows machine ...

good luck....


should be able to right click the icon and stretch it ... if that program installed didn't mess with resizing icons....

---

### Post by carlosgs91 on 2009-06-01
.

---

### Post by ibuclaw on 2009-06-01
> **carlosgs91 said:**
> I used Cairo-Dock but I removed it because it uses lots of space in the screen.

The problem is that I can strech icons but by default .exe icons are too big and have a frame (border).

What icon theme are you using? It looks to be a custom one.

[EDIT]
Just looked at the blog you linked in too.

I notice this following line:
```
convert -resize 48×48 "$2" "$2" # optional
```
The standard icon size is 24x24, that may be why it appears to be so big...

Regards
Iain

---

