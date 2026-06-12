---
title: "[SOLVED] 2nd mouse button lost in compiz!!"
date: 2008-12-15
forum: General Help
---

### Post by the hoplite on 2008-12-15
i've been playing around with compiz, obviously not knowing exactly what possible consequences could there be. so as a result i cannot any longer move my windows around the desktop by clicking on the high end.
and even my 2nd (right) mouse button lost it's functionality. 
somebody help please.. using the latest compiz on a gnome desktop, 

p.s. is there a compiz manual or something because the options are tons of options..

---

### Post by gettinoriginal on 2008-12-15
All of your key bindings are in CCSM under the specifc effect you are trying to adjust.  Here is a how to for compiz, there are others, you just need to google: Compiz fusion on (your flavor of OS)

[http://reformedmusings.wordpress.com/2008/12/09/compiz-fusion-in-ubuntu-810-intrepid/](http://reformedmusings.wordpress.com/2008/12/09/compiz-fusion-in-ubuntu-810-intrepid/)

---

### Post by Forlong on 2008-12-15
> **the hoplite said:**
> i've been playing around with compiz, obviously not knowing exactly what possible consequences could there be. so as a result i cannot any longer move my windows around the desktop by clicking on the high end.
and even my 2nd (right) mouse button lost it's functionality. 
somebody help please.. using the latest compiz on a gnome desktop, 

p.s. is there a compiz manual or something because the options are tons of options..
In case you're on GNOME, you can reset your settings like this:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

