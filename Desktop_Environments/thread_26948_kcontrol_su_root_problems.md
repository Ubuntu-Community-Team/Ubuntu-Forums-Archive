---
title: "kcontrol su root problems"
date: 2005-04-14
forum: Desktop Environments
---

### Post by ykpaiha on 2005-04-14
Hello,
Despite having red a lot of post I still have this prob:
I open kcontrol ok and i can manage everything from there, but when opening a root option (kdm, printer, fonts...) it ask me the password, then after a long wait...nothing back to the menu.
I cleared /var/temp, made the root passwrd, clr home temp etc.. and nothing 
It work with sudo kcontrol!! but not as user?
Any advice pls.

---

### Post by polemicz on 2005-04-14
Post here somewhere. Edit /etc/kde3/kdm/kdmrc and set Allow Root Login to true. For some absurd reason it is defaulted to false.

---

### Post by ykpaiha on 2005-04-14
thanks for your answer but already checked and still no root allowed ?

---

### Post by brenx on 2005-04-14
It worked 4 me, TNX **polemicz** !!

---

### Post by ykpaiha on 2005-04-15
It work now setting up kdm as wm I don'understand why ?In the mean time now noway to use rhythmbox (cannot write on the device!).
Very strange behaviour indeed!!

---

