---
title: "glib trouble"
date: 2006-01-19
forum: General Help
---

### Post by tmahmood on 2006-01-19
So.. I want to develop applications in GNOME.
I installed anjuta, build-essentials, Glade2,  libglib1.2-dev. 
but whenever I try to create a new project in anjuta it gives me an error 
```
you must have glib installed
```
and if I try to compile a glade generated code in terminal gcc also gives me a error 
```
`Glib' has not been declared
```

what should I do :(

---

### Post by jan on 2006-03-24
have exactly the same problem... there seems to be no "glib" in Ubuntu repositories and i dont know how to make Anjuta use libglib2.0 or something like that...

---

### Post by Sabot on 2007-04-26
You need to install libglib2.0-dev to make anjuta recognise your glib.

---

