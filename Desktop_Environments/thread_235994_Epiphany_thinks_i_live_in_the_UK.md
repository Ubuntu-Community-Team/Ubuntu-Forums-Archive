---
title: "Epiphany thinks i live in the UK"
date: 2006-08-14
forum: Desktop Environments
---

### Post by nojjy on 2006-08-14
I get google UK search and various websites think I'm in the UK.  I am not.  I live in the US and A... how do I become a webmerican?

thx

---

### Post by MikeEnIke on 2006-08-14
Are you running through a proxy of any kind?

---

### Post by ramonev on 2006-08-14
Just do **about:config** [enter] on the address bar and change the settings to match the country where you're from:

general.useragent.contentlocale (XX)
general.useragent.locale (yy-XX)

Where "XX" is the location (**US** for example) and "yy" is the language (**en**-US)

Double click an entry will change the values.

(Yep, just like Firefox) :)

---

