---
title: "Problems with Beryl (should I switch to Fusion?)"
date: 2007-07-11
forum: Desktop Effects &amp; Customization
---

### Post by LittleLebowski on 2007-07-11
Every time I use Listen or Thunderbird with Beryl my desktop locks up solid.  I can't even restart X.

  Is this the correct source for Beryl (see below)?  Should I just switch to Compiz Fusion?

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main

---

### Post by Espreon on 2007-07-11
Try Trevihno's respos

 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
 deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Beryl SVN solved lots of problems for me.

---

