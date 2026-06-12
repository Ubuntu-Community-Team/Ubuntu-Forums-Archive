---
title: "How to install linux GLEST ? an easy way ?"
date: 2008-02-08
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-02-08
hello

here the game
:[http://sourceforge.net/project/showfiles.php?group_id=127297](http://sourceforge.net/project/showfiles.php?group_id=127297)

thaks

[http://www.happypenguin.org/images/s05.jpg](http://www.happypenguin.org/images/s05.jpg)

---

### Post by Istonian on 2008-02-08
Search for glest in synaptic and install the package.

---

### Post by frenchn00b on 2008-02-08
> **Istonian said:**
> Search for glest in synaptic and install the package.

nope
[http://www.happypenguin.org/images/s05.jpg](http://www.happypenguin.org/images/s05.jpg)

 apt-cache search glest
I have debian, not ubuntu

---

### Post by Istonian on 2008-02-08
Did not know you used debian. I have not had much success with debian.

---

### Post by Vadi on 2008-02-08
getdeb.net.

If they don't have it, ask them (there's a Contact Us link on the left), and they will.

[http://getdeb.net/search.php?keywords=glest](http://getdeb.net/search.php?keywords=glest)

---

### Post by frenchn00b on 2008-02-09
> **Istonian said:**
> Did not know you used debian. I have not had much success with debian.
it is indeed more complicated cuz you need to compile more stuff your own sometimes. The advantage is that repositories are amazingly huged, and I exactly now what I installed since it was from server install. Works like turbo and very well !

---

### Post by sbrbot on 2008-10-14
There is one problem with compilation/versioning of Glest. Glest is network multiplayer game but for network playing Glest insist on the same version on both network sides. During interconnection Glest checks if the version on both sides is exactly the same; if it is then Glest allows network playing otherwise not. So if on one side is version e.g. **3.1.2-ubuntu** and on another side **3.1.2-getdeb** these Glests wont play over network! So it seems that Glest should be compiled my means not to append any suffix after version number.

---

### Post by Vadi on 2008-10-14
.deb versions aren't the same as game versions though, game versions should be the same.

---

