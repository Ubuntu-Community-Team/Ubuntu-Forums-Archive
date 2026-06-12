---
title: "how do you search for files or folders?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by jinxjinx on 2006-03-03
Hi, whats the best way to do this? can i do it using nautilus? Thanks!

---

### Post by Ramses de Norre on 2006-03-03
I usually use the terminal: ```
sudo updatedb #this will update the database of all the files on your system, this can take a while
locate filename
```

---

### Post by cotcot on 2006-03-04
In nautilus : second last tab of "Locations".

---

### Post by soonindallas on 2006-03-04
in Gnome panel: Places>Search for files

or

in nautilus: Go > search

---

### Post by cbudden on 2006-03-04
If you want something like Google Desktop search, install beagle.

---

### Post by MaX on 2006-03-04
[QUOTE=jinxjinx]Hi, whats the best way to do this? can i do it using nautilus? Thanks![/QUOTE]

Ctrl-F in nautilus

---

### Post by anthro398 on 2006-03-04
Definitly have to agree with previous poster that updatedb and locate are awesome.  I hate having to resort to using find on other peoples servers.

---

### Post by hw-tph on 2006-03-05
I'm surprised nobody has mentioned **find**, one of the most powerful tools you will ever find. Read find(1) for more information.


Håkan

---

### Post by anthro398 on 2006-03-06
Notice that I did, in fact, mention find.  Like any other command that relies on regular expressions, it's very powerful and usually, at least for me, is too unwieldy to deal with most of the time.  I use it when I work on the Solaris servers here, but would rather use locate when I can.

---

### Post by MaX on 2006-03-06
Since I don't know find that well I usually do ```
find | grep whatever
``` in the root if I want to find something, (nowadays I use beagle but before).

---

