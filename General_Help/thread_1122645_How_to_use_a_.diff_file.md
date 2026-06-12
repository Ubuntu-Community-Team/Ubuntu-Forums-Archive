---
title: "How to use a *.diff file?"
date: 2009-04-11
forum: General Help
---

### Post by Bonsanto on 2009-04-11
There is a game "freeciv" I have a problem with my DNS, and to play on multiplayer I need to patch it. But the problem is that I am noob on Ubuntu :(. How I do it? How I patch it? In what directory? Can you tell me exactly the steps, and directories, please? :)

Thanks you so much!.

[http://freeciv.wikia.com/wiki/Main_Page]("http://freeciv.wikia.com/wiki/Main_Page")

---

### Post by Bonsanto on 2009-04-11
Please any suggestion? :)

---

### Post by cubeist on 2009-04-11
you need to open a terminal, and type "man patch"

I know that is a lot of reading, but if I remember correctly, if the patch and the file to be patched are in the same directory, then the basic command is something like
```
patch -p1 patchname < file to be patched
``` 

you could also try the command --dry-run to test the patch for errors before actually applying it.

---

