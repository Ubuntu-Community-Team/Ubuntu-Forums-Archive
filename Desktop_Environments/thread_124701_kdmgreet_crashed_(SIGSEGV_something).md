---
title: "kdmgreet crashed (SIGSEGV something)"
date: 2006-02-02
forum: Desktop Environments
---

### Post by gamerzl on 2006-02-02
i get that everything i tryo to get on to my linux boot. i'm gonna delete teh temp files (~/.kde/tmp-<hostname>, ~/.kde/socket-<hostname>, ~/.kde/cache-<hostname>) Does anybody know why this comes up, or can i switch it back to gnome, form the command prompt? what would the code be?

---

### Post by gamerzl on 2006-02-02
now its gone, no error, but how can i get the gnome login screen back up
i used startx and it booted me into gnome, i've clicked on system, administration, login screen setup, and it never loaded. Is there anything i can do? i'd perfer to get back into kde

---

### Post by joey111 on 2006-02-23
try to delete:
~/.kde/tmp
~/.kde/socket
~/.kde/cache.
it worked for me

---

### Post by jimbren on 2006-02-26
I ran into the same problem when I upgraded to KDE 3.5.1 this morning.  I upgraded kdm and that fixed the problem.

sudo apt-get install kdm

---

