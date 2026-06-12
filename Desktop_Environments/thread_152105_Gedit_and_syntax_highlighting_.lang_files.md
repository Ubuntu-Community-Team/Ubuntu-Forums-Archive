---
title: "Gedit and syntax highlighting .lang files"
date: 2006-03-29
forum: Desktop Environments
---

### Post by pianoboy3333 on 2006-03-29
I was wondering that if I made my own .lang file with the same xml format as the others in /usr/share/gtksourceview-1.0/language-specs/ how could I use it with a text editor? I really don't care what or which it is, even if it was VIM or nano really... I was just wondering if I could.

---

### Post by achim_59 on 2006-03-30
[QUOTE=pianoboy3333]I was wondering that if I made my own .lang file with the same xml format as the others in /usr/share/gtksourceview-1.0/language-specs/ ...[/QUOTE]

I suspect you could do it and it should work. I haven't the time to check it out myself at the moment but maybe on the weekend....

> ...how could I use it with a text editor? I really don't care what or which it is, even if it was VIM or nano really... I was just wondering if I could.

That might be the real issue. It might depend on some other definition file and I don't know what it might be. Maybe you could try it out with a simple self-made syntax or perhaps with EBNF, which is pretty simple and doesn't yet have a .lang,  just to see what happens. To associate a particular editor (say gedit) with that type of file, you might try right clicking on the file in the file browser and choosing "Open with other application" and selecting gedit from the popup Menu. It could well work.

If I find the time to experiment I'll let you know the results. ;)

---

