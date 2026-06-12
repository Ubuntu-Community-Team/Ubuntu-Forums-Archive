---
title: "Using pstricks in Lyx"
date: 2009-05-17
forum: General Help
---

### Post by CHW on 2009-05-17
Hello,

I want to export some Inkscape graphics as a tex-file and use it in Lyx, but I don't succeed. The text compiles, but the graphic isn't inserted in the pdf-file.

So I searched for some examples or tutorials and I found some on wikipedia:
[http://en.wikipedia.org/wiki/PSTricks#Basic_usage](http://en.wikipedia.org/wiki/PSTricks#Basic_usage)

on the pstricks homepage:
[http://www.tug.org/PSTricks/main.cgi?file=examples](http://www.tug.org/PSTricks/main.cgi?file=examples)

and on the Lyx wiki:
[http://wiki.lyx.org/Examples/PSTricks](http://wiki.lyx.org/Examples/PSTricks)

But these examples won't work neither. They compile with errors "Undefined control sequence"

Now I'm asking myself if I have installed every package that I need, I checked, texlive-pstricks is installed, may there be other ones I need?

I would appreciate any help.

Best regards,
CHW

---

### Post by CHW on 2009-05-18
Sorry I posted this by accident. It can be removed.

---

### Post by CHW on 2009-05-18
Update:

I finally managed to compile everything in Kile, but there are still some issues:

* The generated DVI is blank in Evince, but when I open it with Okular I  can see the the drawing. I tried again with Lyx and indeed I could create a DVI and PS file. But converting to PDF doesn't succeed.
It was the same for the other examples in my post before.

* The drawing has very strange colours in the DVI or PS file. It was created with Inkscape and when I export it to PNG everything is OK, I can include it in my document and it has the desired colours.
But when I export it to EPS or TEX then it has a brown background.

I attached two files as ZIP to show you:
1. The PNG which looks OK.
2. The DVI document which I can only see in Okular and has this brown background.

Best regards,
CHW

EDIT: I found a reasonable workaround. It's OK now.

---

### Post by YarDYar on 2010-01-30
> **CHW said:**
> Update:
EDIT: I found a reasonable workaround. It's OK now.

Great - what was it??

Yar

---

### Post by CHW on 2010-01-30
I don't remember exactly what I did, it's already a long time ago ;)
Probably I directly exported the Inkscape drawing as pdf and then included it into the tex/lyx dokument.

In the meantime I do a lot of things with tikz package:

[http://en.wikipedia.org/wiki/PGF/TikZ]("http://en.wikipedia.org/wiki/PGF/TikZ")

It is a very powerful tool and has an excellent documentation with tutorials (see Wikipedia external links).
I don't know if this is what you are looking for, but if you have further questions regarding tikz I will answer if I know.

---

