---
title: "Evolution"
date: 2009-02-21
forum: Desktop Environments
---

### Post by andrea000 on 2009-02-21
Hi everyone,

Every time i check my email evolution comes up and say's enter password for default keyring.I have changed the password for the sudo and the logon but i have to enter the old one to make evolution check the email.
Can anyone help me with this please.


Thank you

XOXOXOXO

---

### Post by Psyphre on 2009-02-21
are you sure it isnt you email password its asking for?

---

### Post by andrea000 on 2009-02-21
> **Psyphre said:**
> are you sure it isnt you email password its asking for?
no my email password is different from my logon password and it is asking for the default keyring i have never heard of it before.

---

### Post by andrea000 on 2009-02-21
Ok i have solved this myself first
i run this in the terminal

mv ~/.gnome2/keyrings/login.keyring ~/.gnome2/keyrings/login.keyring.bkp
echo -n default ~/.gnome2/keyrings/default

then opened evolution and it had me to make 
a new one and gave me the option to save it now 
it works perfect.

---

