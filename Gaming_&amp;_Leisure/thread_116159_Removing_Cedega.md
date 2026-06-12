---
title: "Removing Cedega"
date: 2006-01-12
forum: Gaming &amp; Leisure
---

### Post by Thunk on 2006-01-12
An easy one:

How do I remove Cedega completely? Is searching-deleting the best method? I also want to remove its sub-menu from the Applications menu.

Thanks!

---

### Post by akurashy on 2006-01-12
If you installed it using the deb

sudo apt-get remove cedega

---

### Post by Thunk on 2006-01-12
I didn't, I used the .tgz file

---

### Post by akurashy on 2006-01-12
if you still have the sources, 

type

sudo make uninstall

---

### Post by Cows on 2006-12-26
I installed cedega using .deb package. I typed sudo apt-get remove cedega and it removed some stuff then said cedega wasn't installed but that there were some useless packages installed, to type sudo apt-get autoremove to delete them. So I typed that and it removed the useless packages. After that i check my applications and the Cedega and Wine folder are still there. How do i delete those?

---

### Post by meng on 2006-12-26
rm -r (name of folder)
It is not uncommon for configuration files or other such folders to remain behind after apt-get remove (even after apt-get purge).

---

### Post by Cows on 2006-12-26
Im still new to linux and trying to learn about which folders do wat. I know quite a few already. Can you tell me where the applications folder for the cedega and any future applications are located?

EDIT: BTW .. look at this:

cows@CowsComp:/usr/lib$ sudo rmdir transgaming_cedega
Password:
rmdir: transgaming_cedega: Directory not empty
cows@CowsComp:/usr/lib$

---

### Post by M$LOL on 2007-03-18
*Bump*
I'm having the same problem. I can't get rid of the damn thing. Where does it keep its data?

---

### Post by Perfect Storm on 2007-03-18
```
sudo rm -rf  transgaming_cedega
```

---

