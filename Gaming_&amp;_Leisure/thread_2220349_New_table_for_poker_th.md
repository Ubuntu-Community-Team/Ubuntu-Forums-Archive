---
title: "New table for poker th"
date: 2014-04-27
forum: Gaming &amp; Leisure
---

### Post by newblank25 on 2014-04-27
I'm new to Ubuntu. I have ubuntu 14.04 installed. I downloaded the file for a new table for poker th.  I also extracted files on my desktop. How do i get program to implement the new table?

---

### Post by slickymaster on 2014-04-27
Moved to the Gaming & Leisure sub-forum.

---

### Post by newblank25 on 2014-04-27
thx for response to post. So can someone help?

---

### Post by oldrocker99 on 2014-04-27
OK, your game's tables are installed in

/usr/share/pixmaps/

so:

```
sudo cp <path to files, which should be a .png and an .xpm> * /usr/share/pixmaps/
```

---

