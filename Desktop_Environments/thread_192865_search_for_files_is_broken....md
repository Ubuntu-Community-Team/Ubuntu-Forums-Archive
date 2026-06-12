---
title: "search for files is broken..."
date: 2006-06-09
forum: Desktop Environments
---

### Post by fargoth on 2006-06-09
i can't seem to find files on my HD with the Place->Search for Files...
i mean, it finds files, but not in all the cases...
for example:
the file mldonkey_server is located in /usr/bin, but the search tool wont find any file by that name.
and i can't find giblib either....

how can i make this tool search everywhere and everything and not just what it feels like showing?

---

### Post by patrickfromspain on 2006-06-09
Do you have beagle installed?? I have it, and since then, it will launch under Places -> Search and Applications -> Accesories -> Search instead of gnome-search-tool

That's a little problem, because I think Beagle won't index my root partition (/).

---

### Post by fargoth on 2006-06-09
uh, no, i don't use beagle, i dont want something that will log everything i have into a database... and i dont want mono.

i use the search tool that comes with gnome... should'nt it be able to find any file on my computer?

i set the path to File System, and type *mldonkey* for example... and i know i got in /usr/bin several files that should show up, but they don't!

it must be broken, or misconfigured, because what kind of search tool doesn't show all the results?!

i think it just wont show anything in /usr... any idea why?

---

### Post by oghanchi on 2006-06-09
Have you done updatedb from a terminal? 

Run <sudo updatedb> before searching the file.

---

### Post by fargoth on 2006-06-09
uhm, no, what database am i supposed to update?
i CAN find mldonkey with this tool, but only i tell it to look in folder /usr
if i tell it to look at / it won't find anything! (and i thought / includes it all...)

---

### Post by fargoth on 2006-06-09
ok, wierd... i did what you told me to do, i.e. updatedb and now i can see it all!

can you explain why did this work?
it doesn't make any sense...

---

