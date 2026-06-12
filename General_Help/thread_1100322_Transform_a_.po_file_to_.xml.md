---
title: "Transform a .po file to .xml"
date: 2009-03-19
forum: General Help
---

### Post by pros on 2009-03-19
Hi all,


I need to visually check a completed documentation translation (userguide.gthumb-2-10.el.po).

As far as i understand, it has to be transformed, to be usable in /usr/share/gnome/help/

Any clues?



Thanks

---

### Post by pros on 2009-03-27
Solved

Install poxml tool from repositories

In a folder containing

1. userguide.gthumb-2-10.el.po  (the file we want to check)

2. files gthumb.xml and legal.xml  (from current installation of gthumb 2.10.8 in /usr/share/gnome/help/gthumb/C)

run:

```
/usr/bin/xml2po -e -p LANG.po -o book.LANG.xml book.xml

```
replace book=gthumb  and LANG=userguide.gthumb-2-10.el

file gthumb.userguide.gthumb-2-10.el.xml is what we get.

Rename this file to gthumb.xml and move it to /usr/share/gnome/help/gthumb/C, to view the translation through yelp.

---

