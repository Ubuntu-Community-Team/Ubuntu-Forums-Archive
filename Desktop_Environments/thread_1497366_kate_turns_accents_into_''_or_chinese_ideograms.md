---
title: "kate turns accents into '?' or chinese ideograms"
date: 2010-05-30
forum: Desktop Environments
---

### Post by dargaud on 2010-05-30
Hello all,
I have a problem with opening files with accents with the kate editor. 
They are html files written on Windows, and contain the line
[HTML]<META HTTP-EQUIV="Content-type" CONTENT="text/html; CHARSET=Windows-1252">[/HTML]

Opening in kate, no matter the encoding, messes up the characters. They turn to &#65533; (a '?' in a hexagone) or chinese characters!

What's the proper procedure to open and save those files properly in kate ?

---

### Post by dargaud on 2010-05-30
Well, I found a solution, kinda. If I've never opened and resaved them before with kate, I run [HTML]perl -pi -e 's/Windows-1252/ISO-8859-1/' *.html[/HTML] on them. If I have changed them, then I need to re-edit them, or possibly play with the iconv command if I can figure out an encoding first. Say, if I open them as UTF-8 in kate and see the proper accents, then I can run ```
iconv -f UTF-8 -t ISO-8859-1 MyFile.html > MyFile.html
```
Is that correct ?

---

