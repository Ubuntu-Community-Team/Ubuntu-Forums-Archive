---
title: "Hardy~pidgin is not saving accounts!?!?"
date: 2008-12-06
forum: General Help
---

### Post by KEE on 2008-12-06
i have to  manually enter email and passwords every time i log off and log back on.  Please help !!!

---

### Post by gettinoriginal on 2008-12-07
Accounts > Account > Edit Account > "check" Remember Password

---

### Post by KEE on 2008-12-07
> **gettinoriginal said:**
> Accounts > Account > Edit Account > "check" Remember Password

no I wish it were that easy =(
its ignoring what i check i guess i leave and come back i have to enter my email again and the password. dont matter what i massager i choose also i cant upload pics any more either they are not saving. PLEASE HELP

---

### Post by KEE on 2008-12-07
> **KEE said:**
> no I wish it were that easy =(
its ignoring what i check i guess i leave and come back i have to enter my email again and the password. dont matter what i massager i choose also i cant upload pics any more either they are not saving. PLEASE HELP

the last thing i did was install mac4lin

---

### Post by KEE on 2008-12-07
Please Help!

---

### Post by KEE on 2008-12-07
I tried uninstalling it but it still cant keep any emails logged in and passwords. if i log off and log in it as if its starting for the very first time and asks to add content. Please Help

---

### Post by DesertDude on 2011-05-05
I had the same problem then discovered that my ~/.purple dir was owned by root.  Changing that to my own ID allowed me to save account info and everything worked fine afterwards: sudo "chmod -R *my_id:my_group ~my_id*/.purple"

---

