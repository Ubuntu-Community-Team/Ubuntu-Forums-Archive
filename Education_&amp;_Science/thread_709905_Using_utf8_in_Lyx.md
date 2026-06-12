---
title: "Using utf8 in Lyx"
date: 2008-02-27
forum: Education &amp; Science
---

### Post by DCOVN on 2008-02-27
I am working on a book that uses several languages (including Vietnamese), requiring that I use utf8 encoding. In Lyx when I go to view PDF, PS, or DVI I get a list of errors like this: 

```
Package inputenc Error: Unicode char \u8:&#7899; not set up for use with LaTeX
```

Does anyone know how to set up Lyx to use utf8 encoding in Kubuntu 7.10?

---

### Post by kleeman on 2008-02-28
Are you using texlive packages for your latex installation? Check in synaptic. If so you might try installing the package

texlive-lang-vietnamese

and other similar ones for other languages. The problem you are having is with latex not lyx itself.

---

### Post by DCOVN on 2008-02-28
Thanks for the tip, but I installed as many of the texlive packages as made sense (particularly all the languages that I work with), but the problem is still there. Any other ideas?

---

### Post by kleeman on 2008-03-04
This site might be useful:

[http://texnik.de/cgi-bin/mainFAQ.cgi?file=language/language](http://texnik.de/cgi-bin/mainFAQ.cgi?file=language/language)

In lyx you insert \usepackage commands in Document--->Settings---->Latex preamble

You might also want to ask on the lyx users newsgroup (search gmane for it)

---

### Post by daniel_hh on 2008-06-14
hi!
i had a very similar problem (using cyrillic letters within my german thesis) - after a reinstall (actually radically downgrading from hardy) of gutsy, i couldn't get any output from lyx anymore. ....Unicode char\u8:&#1097; not ...

i solved the problem by purging the gutsy version (1.5.1) and installing the  .deb from gutsy-backports - version 1.5.3 and can handle multiple codes in one document ;)

hope it works for you too!!

daniel

---

