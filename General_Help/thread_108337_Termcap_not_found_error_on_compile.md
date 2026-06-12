---
title: "Termcap not found error on compile"
date: 2005-12-25
forum: General Help
---

### Post by Daegalus on 2005-12-25
Everytime I try to compile MySQL from source I get this error:

```

checking for tgetent in -lncurses... no
checking for tgetent in -lcurses... no
checking for tgetent in -ltermcap... no
checking for termcap functions library... configure: error: No curses/termcap library found

```

And I can't figure out how to get that library.

---

### Post by BathroomNinja on 2005-12-25
Any reason why you are compiling from source and not using apt-get?

---

### Post by akuzminsky on 2008-07-02
Google might be interested in the answer :-)

apt-get install ncurses-dev

---

