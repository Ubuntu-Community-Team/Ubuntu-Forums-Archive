---
title: "--enable-shared option for python installation"
date: 2009-02-09
forum: General Help
---

### Post by mihe on 2009-02-09
Hi,
I am trying to install code aster on ubuntu 8.04.2 64bit. In the readme instructions it says: Python shared libraries are sometimes required ("--enable-shared" option in configure of Python setup).

I have updated python 2.5 with synaptic. How can I check the setup --enable-shared for my python installation? Is there a setup.py ot a .configure file some where that will show me information of my python installation?
Or a command I can run?

Kind regards,
Micke

---

### Post by snova on 2009-02-09
It basically means, "Make sure that when you installed Python, that you installed the shared libraries.". They are present in the Ubuntu packages, so this is of no concern.

But if you're building Python extensions (and I don't know why else it would matter), you will need to install the **python2.5-dev** package.

---

### Post by mihe on 2009-02-10
ok!, thank you.

---

