---
title: "dpkg ERROR  help"
date: 2009-03-08
forum: General Help
---

### Post by interse on 2009-03-08
Using 8.04   In synaptic, an installation stalled and I shut the install down.  

Now when I try to open synaptic I get:
  E: dpkg was interrupted, you must manually run 'dpkg --configure -a'
  E: cache open() failed, please report.

In terminal when I try to run the dpkg --configure -a     I am informed that I need superuser privilege    When I type   'su' I am asked for my password and when I provide it I get the message   authentication failed

HELP    I am using a Dell Netbook with Ubuntu 8.04

---

### Post by zvacet on 2009-03-08
```
sudo dpkg --configure -a
```

---

### Post by interse on 2009-03-08
THANK YOU  zvacet

I was using 'su' instead of 'sudo'

---

