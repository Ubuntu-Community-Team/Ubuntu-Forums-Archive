---
title: "Compiling Dungeon Crawl Stone Soup 0.5, and this happens..."
date: 2009-06-13
forum: Gaming &amp; Leisure
---

### Post by Inquisitorthemad on 2009-06-13
Reposted because the old thread had a very misleading title.

I have all the prerequisites specified in the INSTALL file that comes with the source. However, I still can't get the program to fully install; instead, this happens:

```
make[1]: *** No rule to make target `/usr/include/SDL/SDL_main.h', needed by `acr.o'. Stop.
make[1]: Leaving directory `/home/matthew/Desktop/stone_soup-0.5-src/source'
make: *** [install] Error 2
```

This is not a helpful error message, to put it lightly. What should I do next?

EDIT: Saw an unrelated thread about what "No rule to make target" actually means, and realised I hadn't installed libsdl-dev. Not that this guarantees the compiled product will work but at least it should compile.

---

### Post by OlhoDeChumbo on 2009-07-22
sudo apt-get install libsdl1.2

---

### Post by Sockerdrickan on 2009-07-22
whoah why answer he already solved it :P

---

