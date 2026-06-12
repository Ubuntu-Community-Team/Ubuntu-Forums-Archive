---
title: "I can only connect to my home wireless network"
date: 2009-01-24
forum: General Help
---

### Post by GOODYMAN on 2009-01-24
I'm using EEEBuntu NBR 2.0 on my Asus EEEPC 1002ha.

Installed flawlessly, detected everything even my home wireless network.

But when I went to Panera, I got NOTHING.  No bars.. not a thing.

I ran 

sudo gedit /etc/network/interfaces

and all it showed was..

auto lo
iface lo inet loopback


Is that correct?  What does that mean?

By the way, I'm a NOOB!  :)

---

### Post by xc1024 on 2009-01-24
it shouldn't be. it shows you only the loopback interface, not the actual one.

---

