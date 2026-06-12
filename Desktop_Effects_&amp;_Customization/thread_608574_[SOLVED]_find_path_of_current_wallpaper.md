---
title: "[SOLVED] find path of current wallpaper"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by adityakavoor on 2007-11-10
i have a wallpaper on my desktop, but i cant find it on my harddisk, i really need it
how i can find its path ? , any command ? :confused:

---

### Post by scorp123 on 2007-11-10
Same answer as in the IRC channel :) .... you can try the "find" command. ```
find / -name NameOfWallpaper.jpg -print
``` ... You could also try the "locate" command (locate depends on an indexing service which should run in regular intervals ... so it may not work if you're not running this indexing service!): ```
locate NameOfWallpaper.jpg
```

---

### Post by Forlong on 2007-11-10
In Gutsy, all you have to do is hover your mouse pointer over the image in the "Change Desktop Background" menu (you can access in the context menu of the desktop).

---

### Post by adityakavoor on 2007-11-10
find says "no file or directory"

this is my wallpaper, 01.twp2.monday_normal.jpg
I remember finding it in devianart , cant find even there:(

---

### Post by Forlong on 2007-11-10
[http://manicho.deviantart.com/art/twp2-01-monday-wall-63959975](http://manicho.deviantart.com/art/twp2-01-monday-wall-63959975)

---

### Post by Rinzwind on 2007-11-10
> **adityakavoor said:**
> i have a wallpaper on my desktop, but i cant find it on my harddisk, i really need it
how i can find its path ? , any command ? :confused:

alt-f2
gconf-editor
/desktop/gnome/background

---

### Post by adityakavoor on 2007-11-10
thank you scorp123, forlong, Rinzwind  :popcorn:

I love ubuntu forums:p

---

