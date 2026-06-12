---
title: "Affinity and Awn giving me Segmentation fault (core dumped)"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by gidra on 2007-07-10
Just installed Affinity and Awn successfully but when i run the programs both give me a Segmentation fault (core dumped) error. Any ideas how to fix this please ?

---

### Post by gidra on 2007-07-10
Tried to install Kiba-Dock and same error. I think it has got nothing to do directly with affinity and awn

---

### Post by Vanish00 on 2007-08-05
I get the exact same problem about core dump when I input them in the terminal.  I can get AWN to launch by going through Applications->Accessories->AWN.  When I go to System->Preferences->Avant Preferences nothing happens for me.  Affinity Search doesn't work but Affinity Perferences work when I pick it through System menu.  Anybody got some advice?  I'm using avant-window-navigator-bzr package and affinity package.

---

### Post by francesco_m on 2007-09-10
try this...
get all dependency packages:
> sudo apt-get build-dep affinity

now get the source via svn:
> svn checkout [http://affinity-search.googlecode.com/svn/trunk/](http://affinity-search.googlecode.com/svn/trunk/) affinity-search
(nb. this require subversion package ;)
..and now build affinity:
> cd affinity-search
./autogen.sh
make
sudo make install
(nb. this may require other packages.. gcc, autogen...)

done.. ;)

---

### Post by lucksin on 2007-10-19
you rock dude... finally i got it working..

---

