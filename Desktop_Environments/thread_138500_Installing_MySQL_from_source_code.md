---
title: "Installing MySQL from source code"
date: 2006-03-02
forum: Desktop Environments
---

### Post by sysyphus on 2006-03-02
Not sure wether this is the right sub forum, but here's my problem.

I'm running Unbuntu 5.10 and I'm trying to install mysql 5.0.18 from the source code file using the instructions in the book "Web database applications with PHP and MySQL" published by o'reilly


Ok so here's my problem got everthing running sweet up until I'm asked to configure mysql

>  ./configure --prefix=/usr/local/mysql

so I get this huge list of stuff checking blah, blah.

then:

> checking for nl_langinfo and CODESET... yes
checking for tgetent in -lncurses... no
checking for tgetent in -lcurses... no
checking for tgetent in -ltermcap... no
checking for termcap functions library... configure: error: No curses/termcap library found

I've tried loading in ncurses-base and termcap-compact which was my best guess and no luck, anyone got any bright ideas?

---

### Post by cronholio on 2006-03-02
You need the relevant development libraries. Package names should be the same with an added "-dev" at the end.

---

