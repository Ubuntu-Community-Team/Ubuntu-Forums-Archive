---
title: "Problem installing DeKorator from source"
date: 2005-12-01
forum: Desktop Environments
---

### Post by megadyptes on 2005-12-01
Folks,

I've just started playing around with Kubuntu and have been having difficiult getting [ deKorator]("http://www.kde-look.org/content/show.php?content=31447") installed. The *./configure* seems happy enough, but typing *make* results in the following:
```
/bin/sh: -c: line 0: syntax error near unexpected token `)'
/bin/sh: -c: line 0: `if test ! -f )].in; then  rm -f ./stamp-h2.in;  make ./stamp-h2.in;  else :; fi'
make: *** [)].in] Error 2

```

Being new at this, i've no idea where how to sort this out and get it working. Any ideas?

Ta muchly

---

### Post by GeneralZod on 2005-12-01
It looks to me that the author has messed up his makefile; your best bet would probably be to take it up with him.

---

### Post by dlpfmVfH on 2005-12-15
Try this file... I made on my pc with latest kubuntu 3.5 and checkinstall
see if it works...

---

### Post by megadyptes on 2005-12-21
Hmmm, still no luck, I end up with the following:
```
Unpacking kwin-dekorator (from kwin-dekorator_0.1-1_i386.deb) ...
dpkg: error processing kwin-dekorator_0.1-1_i386.deb (--install):
 trying to overwrite `/usr/lib/kde3/kwin_deKorator_config.la', which is also in package dekorator
Errors were encountered while processing:
 kwin-dekorator_0.1-1_i386.deb

```

Any more ideas?

---

### Post by Freddy on 2005-12-22
Sorry, couldn't read out what was wrong when you compiled, but to give you atleast some hope, I have compiled and installed Dekorator without any problem, didn't find any themes for it that I liked though =).   /// Freddan

---

### Post by eeknay on 2006-02-10
nice one :cool:  the .deb worked fine on drapper *awaytogetskins*

---

