---
title: "Changing QT themes without KDE"
date: 2005-05-08
forum: Desktop Environments
---

### Post by tread on 2005-05-08
This came up in another post I made. I have QT installed (exact package: libqt3c102-mt) which put some libraries in /usr/lib and /usr/lib/qt3.

Now, if I wanted to change the theme, how would I do it? (manually is fine too, I don't necessarily need a tool) I do no want to install kde, if that one package is enough to run QT applications I am happy.

---

### Post by gunnyman on 2005-05-08
sudo apt-get kcontrol.
It's overkill and might install a package or two with it, but you will be able to configure themes, fonts etc.

---

### Post by tread on 2005-05-08
kcontrol needs kde .. which means another 100 mb added to my installation. That is what I am trying to avoid ... I do not use or want kde applications, just qt. 

Sometimes I wonder at the dependencies .. or do all applications in the kde suite require kde? Aren't there any simple qt applications?

---

### Post by tread on 2005-05-08
qt3-qtconfig sorts me out.

---

