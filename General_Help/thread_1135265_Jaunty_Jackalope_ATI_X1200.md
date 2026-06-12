---
title: "Jaunty Jackalope ATI X1200"
date: 2009-04-24
forum: General Help
---

### Post by Jaded Misanthrope on 2009-04-24
Are there any drivers available on Ubuntu 9.04 for the ATI X1200? It worked fine on 8.10, and although I could downgrade back to 8.10 I'd prefer to run 9.04 if at all possible. The card worked fine on 8.04 and better still on 8.10, but all of the drivers seem to have vanished for 9.04: surely drivers are still available?

---

### Post by Jaded Misanthrope on 2009-04-24
Can anyone tell me how to install the drivers for the ATI X1200 on Ubuntu 9.04?

---

### Post by Bateluer on 2009-04-24
Another user was able to use the RadeonHD driver on his X1270, not sure how similar the X1270 is to the X1200 though.

---

### Post by Jaded Misanthrope on 2009-04-24
> **Bateluer said:**
> Another user was able to use the RadeonHD driver on his X1270, not sure how similar the X1270 is to the X1200 though.

Trying the RadeonHD driver can't hurt, I suppose.

---

### Post by Jaded Misanthrope on 2009-04-24
Installing the RadeonHD drivers doesn't seem to have helped at all. I don't want to have to reinstall 8.10 unless that's the only way to use my X1200, but at the moment that seems to be the only option. Any advice would be greatly appreciated.

---

### Post by Rainstride on 2009-04-24
> **Bateluer said:**
> Another user was able to use the RadeonHD driver on his X1270, not sure how similar the X1270 is to the X1200 though.

hmmm.... I wonder if that would work with my x1300.... or if it is even worth trying compared to the open source drivers.

---

### Post by dael99 on 2009-05-12
> **Rainstride said:**
> hmmm.... I wonder if that would work with my x1300.... or if it is even worth trying compared to the open source drivers.

in the description of the package looks like this is compatible with X1300

but, how long will it take to develop drivers for this kernel??

---

### Post by ugm6hr on 2009-05-24
On my X1200, I got the radeonhd driver to work properly.  Unfortunately, I need TV-out, so am still looking for a solution....

PS: I cannot get the default -ati driver to work at all.  I have another thread about that.

---

### Post by imbjr on 2009-05-24
The HD drivers did not give any extra advantage in the use of my X1300 card.

I don't play games much these days, but it's a shame I no longer have the option of running them flawlessly now, unless I go back to 8.10.

---

### Post by xaviermerino on 2009-05-28
This might sound interesting. Jaunty uses Xorg 1.6 which is unable to support ATI fglrx for certain models. I downgraded Xorg to 1.5.2 (the one Intrepid uses). However I can't seem to make the drivers (ATI Propietary Linux Drivers from ati - Manual Installation). Maybe you can make it work. I think it doesn't work, because I get an odd error. But maybe you guys can try it, after all Jaunty can use Xorg 1.5.2, and if you ever need to restore your Xorg using xfix can be of help. :p

---

