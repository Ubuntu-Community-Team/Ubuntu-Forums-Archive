---
title: "noob - how to uninstall madwifi?"
date: 2006-05-10
forum: Desktop Environments
---

### Post by Banter on 2006-05-10
Hey, I'm new to linux. One of the big problems I have with it is that it is difficult for me to uninstall programs. Which leads me to the question . . .

how do you uninstall madwifi?

---

### Post by nanotube on 2006-05-10
what method did you use to install madwifi?

if you installed it with apt-get or synaptic, you can just open up synaptic, find the package in there, and mark it for "complete removal", then hit apply - that will uninstall it.

if you installed it from a source tar.gz file, then go to the directory where you did the 'make install' and type 'make uninstall'.

for a good tutorial on the various methods of installing/uninstalling software, see the second link in my sig.

---

### Post by Banter on 2006-05-12
Thanks for the advice! I think i did it with apt-get -i so ill try looking in synaptic.

---

