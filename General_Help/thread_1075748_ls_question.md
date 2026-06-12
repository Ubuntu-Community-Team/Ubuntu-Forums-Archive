---
title: "ls question"
date: 2009-02-20
forum: General Help
---

### Post by inanutshellus on 2009-02-20
So someone asked me today "how do I list out the only hidden files in a directory?"

So I quipped back

```
ls -a
``` (duh)

No no, ONLY the hidden files. 

Oh. Uh...

```
ls -a .*
```

No... that does some weird craziness printing out the contents of multiple directories. 

Wha, really? 

Yeah...

So... I finally ended up with this:

```
find . -maxdepth 1 -name ".*"
```

but... what if you wanted file attributes like size and such that "ls -**l**a" would get you? find doesn't display that. Surely there's a way to get ls to be non-recursive when doing "ls -a .*". 

Right? =/

---

### Post by geirha on 2009-02-20
find has an -ls option which lists files similar to ls -l ...

And with -printf you can cherry pick what information to print. Read find's manual:
```
man find
```

---

### Post by CrucifiedEgo on 2009-02-20
Here's what I came up with:

ls -a1 | grep "^\." | ls -lhd

---

### Post by mcduck on 2009-02-20
Interesting question. :) This seems to work, but not with "ls -la":
```
ls -a | grep '^\.'
```
I'm not sure if there's any way to do this with a single command, as "." alone would mean the current directory as well as being a character usable in file names..

edit: too slow. :D

---

### Post by geirha on 2009-02-20
If you don't mind seeing the special . and .. directories, then ```
ls -ld .*
``` is also an option.

---

### Post by inanutshellus on 2009-03-02
> **geirha said:**
> If you don't mind seeing the special . and .. directories, then ```
ls -ld .*
``` is also an option.

Ah HAH! -d!! Thank you!

---

