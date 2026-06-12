---
title: "Nautilus won't open OpenOffice.org documents"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Corvillus on 2006-06-03
For some reason, Nautilus won't open OpenOffice.org documents directly on a double-click. It works if I manually type the command into the terminal, and it works if I actually drag the document icon onto a launcher for the given application, but I cannot make it work when I actually directly open the file from nautilus. I've tried adding an association for it, specifically typing the given command in, and that doesn't work. I also even tried adding associations for the alternate launch syntax (oowriter as opposed to ooffice -writer for example), and it still doesn't work. Has anyone else experienced this issue, or have a solution for me?

---

### Post by bluevoodoo1 on 2006-06-03
Perhaps this might work. 

Right-click on an OO.org document, head to "properties," then "open with," select OpenOffice. That should associate OpenFooice.org with all/most OO.org documents.

---

### Post by Corvillus on 2006-06-03
Nope, I did that. It's associated with OOo, it just won't open. You can even see it in the Window List saying Opening <filename>... and the spinner going, but no OpenOffice.org splash screen, or any other indication that OpenOffice.org is even being opened. Also, just to try something else, I even associated a .txt file with OpenOffice.org Writer to see what would happen, and it didn't open. For some reason Nautilus refuses to launch OOo at all. Thanks for the suggestion though.

---

### Post by BoyOfDestiny on 2006-06-03
[QUOTE=Corvillus]Nope, I did that. It's associated with OOo, it just won't open. You can even see it in the Window List saying Opening <filename>... and the spinner going, but no OpenOffice.org splash screen, or any other indication that OpenOffice.org is even being opened. Also, just to try something else, I even associated a .txt file with OpenOffice.org Writer to see what would happen, and it didn't open. For some reason Nautilus refuses to launch OOo at all. Thanks for the suggestion though.[/QUOTE]

That is bizzare. If you launch nautilus from terminal, does it spit out any errors when you try launching the files?

---

### Post by Corvillus on 2006-06-03
Nope, but Nautilus also runs as a background process when I run it from the terminal, which doesn't really help.

---

### Post by Corvillus on 2006-06-03
Nevermind, it turns out Nautilus just was messed up for some reason, and a simple killall nautilus fixed it.

---

