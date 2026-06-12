---
title: "rxvt transparency"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by dijxtra on 2007-05-04
I tried google, but nothing found there works for me. I have brand new, 3 hours old installation of Ubuntu 7.04, and the newest rxvt-unicode. How do I make the terminal transparent? :-)

---

### Post by Pox on 2007-05-04
Are you running a Compositing Window Manager such as Compiz or Beryl? You'll have little luck without one.

---

### Post by dijxtra on 2007-05-05
No, I'm not. I don't like those fancy thingies.

---

### Post by Pox on 2007-05-05
Well unless you mean the fake transparency which gnome-terminal/xfterm offers, you're out of luck... I'm not familiar with rxvt myself.

---

### Post by x1a4 on 2008-04-19
Hi,

For pseudo transparency add the following to ~/.Xdefaults
```

rxvt*transparent:          true
rxvt*shading:              *n*
rxvt*tint:                 *colour*
rxvt*inheritPixmap:        true

```
Where *n* is the shading value, the lower it is the darker the background.
Where *colour* is the tint colour. 

For true transparency install and run **transset *n***, then click the window you wish to set transparency to.  Where *n* is a value between 0 and 1.  0=invisible 1=fully opaque.  An example would be: 
```
transset .7
```

You need a compositing manager for transset to work.  **xcompmgr** is a nice, small, generic compositing manager you can use.

Both transset and xcompmgr are in the repositories.

---

