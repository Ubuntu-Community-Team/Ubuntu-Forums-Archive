---
title: "Programming a GUI with Xubuntu"
date: 2009-05-31
forum: Desktop Environments
---

### Post by Liminalitus on 2009-05-31
Hello all. I'm a bit of a (super) newbie when it comes to Xubuntu, and this seems like a great site to ask questions. My question is this: If I want to go about writing a GUI for a program in Xubuntu, how would I do that, and would it work on all other Ubuntu OS's? And can I use C++? Sorry if my English is bad.

---

### Post by Linteg on 2009-05-31
XFCE and Gnome both use the GTK+-toolkit. If you want to develop GUI apps with C++ I'd recommend using gtkmm (which is a C++ interface for GTK). The development package required should be available as libgtkmm2.4-dev, you'll also need g++ (GNU's C++ compiler) and pkg-config, they're all available in Xubuntu's repositories so install them with Synaptic (or Add/Remove Software).
gtkmm documentation is available at [http://www.gtkmm.org/documentation.shtml](http://www.gtkmm.org/documentation.shtml).

---

### Post by Liminalitus on 2009-05-31
Ah. That helps me very much. Thank you, friend.

---

