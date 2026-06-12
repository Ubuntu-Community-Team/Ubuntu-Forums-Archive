---
title: "Programs closing instantly when opened"
date: 2009-02-26
forum: General Help
---

### Post by notoriousmic24 on 2009-02-26
A bunch of programs are closing instantly when I try to open them. Synaptic Package Manager, Add/Remove Program, Package Installer...ect. They flash for a second and then close

Im running Intrepid Ibex on my Dell E1505 Laptop. Any ideas?

---

### Post by smani on 2009-02-26
Run them from the terminal and see if they leave an error message. If you do not know what's the name of the executable of the program, you can look at the menu editor and at the properties of the item in question.

---

### Post by jmszr on 2009-02-26
notoriousmic24,

                I run 8.04 and something approximating this happened early on. My Synaptic, Update Manager,and Add/Remove would start loading and then just fade away. The fix was```
sudo rm /var/cache/apt/*.bin
```  Hope this helps.

---

### Post by notoriousmic24 on 2009-02-27
jmszr, Thanks a bunch. That seemed to do the trick.

---

### Post by notoriousmic24 on 2009-02-28
Now deluge for some reason is doing the same thing...and help?

---

