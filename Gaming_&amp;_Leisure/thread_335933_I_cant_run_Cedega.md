---
title: "I cant run Cedega"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by comegalletas on 2007-01-10
Hi there I just bought Cedega, and cannot run it I get this error:


(Point2Play_gui.py:7764): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 44, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

Transgaming is in silence for already 2 weeks, can someone help me ??

Thank you

---

### Post by Z3n0s on 2007-01-11
What version of Ubuntu are you running? :-k

---

### Post by comegalletas on 2007-01-12
Edgy... latest release.. full install not live cd

---

### Post by comegalletas on 2007-01-12
Help someone, I have paid three months for nothing !!

---

### Post by Perfect Storm on 2007-01-13
It's a common problem if you run cedega on a non-english setup. As far as I know Transgaming are working on the problem.

---

### Post by edemark on 2007-01-13
Hi 
Luckily i have never had this problem though i always install linux in english and use the diferent languages that i need only at the level of gui lets say gnome. I am sure that you can reconfigure system language somehow. My first guess would be apt-get but i am not so sure (you might ask as a separate thread in some other forum, not in games, or search if there is a how-to abaut it). Then you might get rid of this problem.

pd as it is actually sad abowe

---

