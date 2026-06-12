---
title: "cannot open synaptic package manager or add remove programs"
date: 2009-03-03
forum: General Help
---

### Post by mejbr2003 on 2009-03-03
I was trying to install adobe flash...now I cant do either of these things ....the synaptic says Ihave  a program running, but I dont

---

### Post by zvacet on 2009-03-03
What if you restart your comp?Do you get same message?

---

### Post by mejbr2003 on 2009-03-03
yup

---

### Post by adult swim on 2009-03-03
go to a terminal, Applications>accessories>terminal, then enter in ```
pidof apt-get
``` it should return a number.  if it does then run ```
sudo kill -9 xxxx
``` and replace xxxx with the number.  then try to open synaptic-package-manager

---

