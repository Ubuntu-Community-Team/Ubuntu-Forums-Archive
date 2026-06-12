---
title: "Not really sure....??"
date: 2009-01-10
forum: General Help
---

### Post by Kaneda187 on 2009-01-10
Ah I have a problem...My girlfriend recently tried to update not exactly sure what update it was but when she went to do so it gave a warning that someone could be eavesdropping on sure session or your keyboard is not responding...whatever that means??
Well since this happened the desktop just seems buggy it gets all slow and you cant open the apps, places or system. I really dont have a clue whats going on also in firefox some pages appear either really big font and pictures or really small! so PLEASE HELP!! 
I at least want to find out what the hell caused it as it seems very strange and weird, i never had a problem like it anyways!
thanks in advance.

---

### Post by Kaneda187 on 2009-01-10
anybody??

---

### Post by taurus on 2009-01-10
Which release are you running?  Did you install Ubuntu on it own partition or did you use wubi?

---

### Post by Kaneda187 on 2009-01-10
im running ibex dual booting with vista...

---

### Post by mgol on 2009-01-10
You can check which packages has changed its state (for example were installed or updated) most recently by viewing /var/log/dpkg.log contents. Last changed packages are listed last, for example to list 20 last changes You can enter this:
```
cat /var/log/dpkg.log | tail -20
```
in the terminal.

---

