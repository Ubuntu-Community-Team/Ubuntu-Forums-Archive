---
title: "Does ubuntu have C compiler?"
date: 2005-02-19
forum: Desktop Environments
---

### Post by napalm_death on 2005-02-19
do ubuntu have C compiler? thanks

---

### Post by alastair on 2005-02-19
Yes, ofcourse. It has gcc and others.

Try installing something like "build-essential", then in a shell type :

gcc -v

to see the C compiler version.

---

### Post by drasko on 2005-02-19
Yes... shure thing...
Compile something with gcc foo.c foo, that will produce executable foo, and execute it with sh foo or ./foo from the current directory to see if it works...

Good luck,
Drasko

---

### Post by CyBEr-GaNgE on 2005-02-24
Wonder why some gdb front-ends are not included into CD...

---

### Post by toojays on 2005-02-24
Emacs is included, and that has a gdb frontend in it. :)

---

### Post by bored2k on 2005-02-24
[QUOTE=toojays]Emacs is included, and that has a gdb frontend in it. :)[/QUOTE]

might i suggest apt-getting 
Anjuta Integrated Development Environment ?
Scite Progamming editor

---

### Post by CyBEr-GaNgE on 2005-03-07
Thank you for the emacs suggestion.

bored2k, the point is not about apt-getting something, the point is to have a friendly debugger available when using the live distribution or when installing a minimal system.


ciao

---

