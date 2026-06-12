---
title: "natbib citet in numerical mode"
date: 2009-08-05
forum: Education &amp; Science
---

### Post by ad_267 on 2009-08-05
When using citet in numerical mode with natbib, I expect to get something like "Author, 2009 [1]", but instead I just get " [1]". I've tried with a minimal example using only the natbib package and a few different numerical bibliography styles but I still get the same result. Am I missing something or is something wrong here?

---

### Post by ad_267 on 2009-08-05
Ok it was just the bibliography styles I was using which were causing problems, using abbrvnat and unsrtnat works.

---

### Post by XCan on 2009-08-06
There is this neat program called bibit [http://sourceforge.net/projects/bib-it/](http://sourceforge.net/projects/bib-it/) which lets you fairly easily design your own bibstyle. Be wary though that careless freestyling will just end up with you breaking the typographical rules.

---

### Post by ad_267 on 2009-08-06
Ok thanks for pointing that out. At the moment I've just changed the abbrvnat.bst file slightly but I'll have a look into using bibit.

---

### Post by ad_267 on 2009-08-12
For anyone else who comes across this thread, I also found that running "latex makebst" is a good way to generate a bibliography style. Something that doesn't seem to be mentioned anywhere is that if you want it to be compatible with natbib you have to select the "Author-year with some non-standard interface" option rather than numerical, even if you want to use natbib in numerical mode.

---

