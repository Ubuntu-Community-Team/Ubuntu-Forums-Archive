---
title: "gutenprint 5.0 packages anywhere?"
date: 2005-12-22
forum: General Help
---

### Post by Kirk Wolf on 2005-12-22
Has anyone built packages for gutenprint 5.0.0-rc1? 

Thanks, 
Kirk

---

### Post by BathroomNinja on 2005-12-23
All I'm finding is the source.  Are you unable to install from source?

---

### Post by Kirk Wolf on 2005-12-23
I've downloaded the source, and ./configure and make seems to work.

Btw - are the default options for building gutenprint from source sufficient?

I haven't done a "make install" yet, since I'm worried about whether it will break my currently working system.   gutenprint seems to install a lot of stuff, and I'm a little worried that I won't have a clean way of backing it out if something goes wrong.   If I used deb packages, I would more easily be able to uninstall and reinstall the unbuntu-level gimp-print packages.

Can anyone explain what would have to be done to "back out" gutenprint if I installed from source?  (on a breezy system)

Thanks, 
Kirk

---

### Post by Kirk Wolf on 2005-12-25
I think that I found an answer to the important question: "How to I safely install from a non-debian source build".

[http://www.debian-administration.org/articles/147](http://www.debian-administration.org/articles/147)

---

### Post by hoodwink on 2005-12-26
[QUOTE=Kirk Wolf]I think that I found an answer to the important question: "How to I safely install from a non-debian source build".

[http://www.debian-administration.org/articles/147](http://www.debian-administration.org/articles/147)[/QUOTE]
Looks like a good procedure, but ... checkinstall segfaults on my dapper system:mad:

---

