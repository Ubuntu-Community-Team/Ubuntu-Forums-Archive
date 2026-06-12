---
title: "Trying to instal LiVES, I get missing gtk+-2.0 error..."
date: 2009-01-24
forum: General Help
---

### Post by tiggsy on 2009-01-24
This thread (which is read only) gives me half the answer:

> It was helpful to mel to find out that
gtk+-2.0 = libgtk2.0-dev

but doesn't say how to tell configure about it. I cant make head or tail of the configure help file - or the pkg-config man page.

(yeah, I know. I'm stoopid)

---

### Post by fragos on 2009-01-24
[http://www.getdeb.net/search.php?keywords=lives](http://www.getdeb.net/search.php?keywords=lives) will give a package matched to your version of Ubuntu.

---

### Post by tiggsy on 2009-01-28
Thanks - but when i ran it i got 

```
Error. Dependency is unsatisfiable: libgtk2.0-0
```

---

### Post by fragos on 2009-01-28
If you're running Ubuntu 8.10 that package is available and supported. Search for it with Synaptic and it should say version 2.14.4-0ubuntu1 is latest available.

---

### Post by tiggsy on 2009-01-29
Oh dear. Not really in the mood for upgrading. Hardy 8.04 Heron suits me just fine. 

Can't I set up a translation for gtk+-2.0 => libgtk2.0-dev somewhere/somehow?

---

### Post by fragos on 2009-01-29
[http://getdeb.net](http://getdeb.net) has different packages for each Ubuntu release 32 and 64 bit release. Make sure you've downloaded the correct one. I'm registered with the site and they automatically offer me the correct version.

---

### Post by tiggsy on 2009-01-29
Aha! Yes, it was offering Intrepid. I swapped to Hardy and now I have it running. 

Thank you!

I'm sure that getdeb place will be useful in the future as well.

---

