---
title: "working with mp3s?"
date: 2005-08-12
forum: Desktop Environments
---

### Post by sal on 2005-08-12
im looking for an app to join mp3 files together.
something simple.
in winblows i was using BL join:
[http://www.brawnylads.com/modules.php?name=Content&pa=showpage&pid=30](http://www.brawnylads.com/modules.php?name=Content&pa=showpage&pid=30)

im looking for something similar.
thanks

---

### Post by wmcbrine on 2005-08-12
Looking at that page, it isn't even an MP3 joiner per se, just a simple concatenator -- equivalent to "copy /b", according to their own blurb. So, if that works for you, you can do it just as easily in Linux with "cat":

cat file1 file2 > bigfile

That said, there's also a dedicated program called "mpeg3cat"... it seems to be part of the libmpeg3 package. Like cat, it's a command-line tool.

---

### Post by sal on 2005-08-17
this was exactly what i needed. thanks a million it works perfect for what i had to do.

---

