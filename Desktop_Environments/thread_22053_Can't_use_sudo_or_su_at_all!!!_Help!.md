---
title: "Can't use sudo or su at all!!! Help!"
date: 2005-03-25
forum: Desktop Environments
---

### Post by wk1989 on 2005-03-25
Hi, I got this REALLY weird problem. Today I booted up Ubuntu, and I tried to run Synaptic using
"sudo synaptic"
and it fails to run and tells  me "sudo must be setuid"

so then I tried to use su, it asks me for the password, I enter the correct password but it tells me "authentication failed!" 
and idea why this happens and what can I do to fix it? cuz I really don't want to reinstall!!!
 ](*,)  ](*,) 

thx!!!

---

### Post by az on 2005-03-25
Boot into recovery mode and type

passwd <yourusername> <yournewpassword>


If you no longer have the grub entry for that, add init=/bin/bash in your current grub kernel line.

---

