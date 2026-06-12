---
title: "zbmanuscript font?"
date: 2008-07-01
forum: Education &amp; Science
---

### Post by elj4176 on 2008-07-01
My wife is a teacher and I have converted her new laptop to Hardy and she is getting along fine. One thing she asked for was a font called zbmanuscript (zaner-bloser). It is a handwriting font for teaching the kids to write.
Anyone know how to install it? She has it on a CD and installed it for xp a few years ago so getting the font is not a problem.

thanks!

---

### Post by kostkon on 2008-07-01
I assume is a TTF font. You can simply copy it to the hidden *.fonts* folder that exists in her home folder. If this folder does not exist, just create it yourself.

---

### Post by elj4176 on 2008-09-08
I just got around to trying this and the fonts work in gedit but not openoffice. I looked on openoffice.org and they pointed to a non-existant folder /usr/X11R6/lib/

Any other help here?

---

### Post by kjohansen on 2008-09-08
Try this from the .font folder
```

sudo fc-cache -f

```

stolen from [http://ubuntuforums.org/showthread.php?t=493456](http://ubuntuforums.org/showthread.php?t=493456)

---

