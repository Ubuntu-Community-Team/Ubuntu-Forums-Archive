---
title: "i think you already ask this"
date: 2005-10-23
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-10-23
i just cannot configure my mouse i´ve tried everything any suggestions
mouse: genius ps/2 optical mouse with scroll wheel

---

### Post by stuporglue on 2005-10-23
Does the light come on when you plug it in? 

What happens if you do 
$ sudo cat /dev/input/mouse0 
then move your mouse arround?

Try the same thing for each item listed in /dev/input and see if it prints anything when you move your mouse.

---

