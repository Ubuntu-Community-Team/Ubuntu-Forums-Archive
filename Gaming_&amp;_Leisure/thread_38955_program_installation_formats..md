---
title: "program installation formats."
date: 2005-06-02
forum: Gaming &amp; Leisure
---

### Post by dphipps on 2005-06-02
To install programs on ubuntu linux what type of file do I need, and is there anything special that I need to do?  I can get .rpm, .deb, or, .tgz formats but I am not sure of how to install any of them.

---

### Post by SGC on 2005-06-02
For ubuntu use .deb packages, and install them with the following command:
dpkg -i PACKAGE_NAME.deb

---

### Post by az on 2005-06-02
...but you are better to just stick with what is in the repositories.

You can compile and install any software you want.  Packages are precompiled, meaning they were compiled un a certain environment and if you are not running them in the ienvironment they were meant for, thay may break.

Add Universe and Multiver to your synaptic repositories and you should be able to find any packages you want...

---

