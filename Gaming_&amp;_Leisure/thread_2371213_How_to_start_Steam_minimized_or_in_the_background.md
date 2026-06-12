---
title: "How to start Steam minimized or in the background"
date: 2017-09-12
forum: Gaming &amp; Leisure
---

### Post by borg101 on 2017-09-12
I'm running 17.04 and I have Steam run on startup.  Does anyone know if I can just have this run silently in the background or start minimized?

---

### Post by Perfect Storm on 2017-09-12
try with
```
steam -silent
```

---

### Post by borg101 on 2017-09-12
> **Artificial Intelligence said:**
> try with
```
steam -silent
```
Where do I insert that line?  Terminal?  I want this to happen on boot.

---

### Post by Perfect Storm on 2017-09-13
Press <alt>+<F2>
```
gnome-session-properties
```

Then add.

---

### Post by borg101 on 2017-09-14
> **Artificial Intelligence said:**
> Press <alt>+<F2>
```
gnome-session-properties
```

Then add.

Thanks!  That worked.

---

### Post by tatsuya6400 on 2018-08-21
For anyone not using gnome, open whatever counts for your "startup applications" and edit the steam entry from:
```
/usr/games/steam %U
```
to
```
/usr/games/steam -silent %U
```

---

### Post by oldrocker99 on 2018-08-22
That answer is 100% correct, and tatsuya6400 is due the thanks of a grateful world, or at least those of us who, for good reason IMHO, don't use GNOME.

---

