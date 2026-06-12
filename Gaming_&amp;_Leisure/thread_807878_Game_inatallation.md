---
title: "Game inatallation"
date: 2008-05-26
forum: Gaming &amp; Leisure
---

### Post by Aralon56 on 2008-05-26
Hi could you tell me what programmes are used to install games thanks :D

---

### Post by jpeddicord on 2008-05-26
That's pretty generic question. Games can be installed in many ways:

[LIST]
[*]Applications > Add/Remove
[*]System > Administration > Synaptic Package Manager
[*].deb downloads from a web site
[*]Source downloads from a web site
[/LIST]

The first three are preferred methods of installing games, as all of the software can be easily removed the same way. Installing by source code is not only difficult, but it can also be hard to remove once installed. If you do find a tutorial that tells you to install a game from source, use [checkinstall]("apt:checkinstall") instead:
```
./configure
make
sudo checkinstall
```

That will install the game in a similar method to the third option above, allowing you to remove it easily later.

---

### Post by Perfect Storm on 2008-05-26
Note: checkinstall only work with some(few).

AFAIK, to use checkinstall correctly you need to use auto-apt when configuring the source codes.

auto-apt run ./configure <flags> <flags> etc.
make
checkinstall --install=no
sudo dpkg -i *.deb

You can only use checkinstall on sources that comes with configure files that have to be run like shown above. It won't if scons/python/etc. is required for compiling.
If checkinstall --install=no fails use sudo make install instead.

---

### Post by Aralon56 on 2008-05-26
i ment what programes do use to install window games like warcraft

---

### Post by Perfect Storm on 2008-05-26
wine. Check our wine forum for more info regarding setting it up and how to play it.

---

### Post by vectorslave on 2008-05-26
Try Wine or Cedega.

---

