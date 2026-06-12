---
title: "scripting assistance?"
date: 2009-02-22
forum: General Help
---

### Post by gakuma on 2009-02-22
I'm looking to create a BASH script that searches all of my users home directories for threatening words. (bomb, kill, gun, steal, etc).  I tried running a 

find / | grep -r "searchterm"

as root, however, it would only display file names, not look within the files for those words.

Is there something I'm missing?

---

### Post by bc90021 on 2009-02-22
Hi,

I'm not much of a guru at this sort of thing, but this page was helpful to me:

[http://www.gnu.org/software/grep/doc/grep_13.html](http://www.gnu.org/software/grep/doc/grep_13.html)

Basically, you don't need the find part - grep can search recursively.  Alternatively, you want to look into "xargs" or "print".

---

### Post by timvoet on 2009-02-22
try 
find / | xargs grep -ir "searchterm"

you already knwo what the find does, the xargs passes that file into the grep, the -i is ignore case, -r is recursive

Tim

---

### Post by gakuma on 2009-02-22
> **timvoet said:**
> try 
find / | xargs grep -ir "searchterm"

you already knwo what the find does, the xargs passes that file into the grep, the -i is ignore case, -r is recursive

Tim

Aha! That did it!

Thank you. :D

---

