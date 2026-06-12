---
title: "[SOLVED] text files become corrupt with gedit etc"
date: 2008-12-07
forum: General Help
---

### Post by yxlbaz on 2008-12-07
Hardy Heron  2.6.24-22

I can create, edit, save and re-edit a text file OK with vi

If  try to open it with gedit the type changes to "unknown" in Nautilus and I get a message about unknown encoding and it won't open.  After this the icon changes and everything seems to think that it's a binary file and even vi shows it like a binary file - just symbols etc.

Any ideas?

baz

---

### Post by geirha on 2008-12-07
That sounds odd. If you create a new file with gedit that only contains the letter a, and also edit a file created by vi to only contain the letter a, then run hd (hexdump) on it in a terminal
```
hd *file.txt*
```

It should only have 0x61 and possibly 0x0a if it adds a new line, but what does gedit put instead?

Also, try the same with a non-ascii character.

---

### Post by yxlbaz on 2008-12-07
Thanks geirha

This is what I've done -

Use vi to make f1.txt with just "a"

 hd f1.txt
00000000  61 0a

Nautilus shows f1.txt as "plain text file"

Double-click on f1.txt in nautilus and file size increases to 4k (from 2k I think).  File not loaded

OK - hold it right there!  Eureka moment!  I feel a bit of a twonk!

Just noticed that the default application for opening txt files is "_shred_".  I think I did this a few weeks ago by mistake.

Thanks again.  Your reply made me analyse it better.

---

