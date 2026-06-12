---
title: "Remove PHP5"
date: 2009-04-08
forum: General Help
---

### Post by quikone8 on 2009-04-08
Hi, I have another post going on the subject, but would like to ask the question a different way.  I have had PHP5 running but had some gd library problems.  I installed a PHP version from dotdeb and I would like to remove it.  So far everything I have tried through terminal has been unsuccessful.  Can or will anyone tell me how to remove any instance of php5 so I can do a fresh install.  Or is there a way that I can force a rewrite or new install to boot out the non-working package?

---

### Post by wajjs on 2009-04-08
Try: 
aptitude search php5

to see what php packes you got installed. (its an i in front if it's installed)

then do:

sudo aptitude purge php5-package1 php5-package2

---

### Post by quikone8 on 2009-04-09
Installed php5mysql

---

