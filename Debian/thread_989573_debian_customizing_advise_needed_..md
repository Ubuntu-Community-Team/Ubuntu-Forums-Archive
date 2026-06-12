---
title: "debian customizing advise needed ."
date: 2008-11-21
forum: Debian
---

### Post by cmay on 2008-11-21
hi. i have a debian etch on a older computer with 600 mhz and 300 mb ram i would like to have running as fast as possible . i need to use a light windowsmanager but i cant seem to find cde in the repositories. i have installed the very few programs i need for it. if ohter than cde i should choose a windows manager what would be a good choice . i am not going to use fluxbox i think .anohter thing is i cant figure out how to edit my sources list. maybe i mispell when i try to do it from nano but it gives not the etc.apt.sources file to edit. is it not right to edit /etc/apt/sources.list  ???.

---

### Post by oOarthurOo on 2008-11-21
```
su -
nano /etc/apt/sources.list
```

[http://oreilly.com/catalog/debian/chapter/book/ch06_03.html](http://oreilly.com/catalog/debian/chapter/book/ch06_03.html)

---

### Post by cmay on 2008-11-21
thanks . i will use afterstep i think. i did misspell the sources list. been too long since i used debian . i am very happy for this t helped a lot.
thanks for the time.

---

### Post by cmay on 2008-11-21
done. it was aftestep i was looking for. i use cde on solaris so i would liked that. but it is not there. kde is way too heavy and so is gnome. but afterstep is just good . i used it once before but  could not remember the name of it. thanks  again for the links.  :)

---

### Post by kerry_s on 2008-11-21
debian rocks on those specs.
i'm using debian lenny custom install on 450mhz 256mb ram.
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

i did mine from the base install up. at the package selection i unchecked everything. so after you finish and reboot you'll be at command line.

then:
log in as root
apt-get install xorg
(that gives you the X stuff needed by the wm/de)
apt-get install afterstep aterm
(that's enough to get you into X, i'm a jwm fan, but use what ever makes you happy)
log out of root, type> exit
log in as your regular user
type> startx

open your term and continue building, i usually grab synaptic and go visual at that point.
su
apt-get install synaptic
gksu synaptic &
type> exit <if you no longer need the term.

mine:

---

### Post by markharding557 on 2008-11-27
the xfce desktop will fly on 600mhz/300ram

---

