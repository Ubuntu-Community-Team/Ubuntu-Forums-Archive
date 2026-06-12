---
title: "Root Password?"
date: 2005-08-21
forum: Desktop Environments
---

### Post by Linux_Noobie on 2005-08-21
Well yesterday i made the switch to ubuntu and plan on mainly using it after i get a internet on it (Using a labtop right now) so now i just need to know something..What is the root pass? I tried to do something in root but when i tried it just said.
> Failed to Run[Path to Program] Child Failed with 1-status 
So what does that mean o.0 I never set my root pass but used mandrake linux before and had it set but have no clue now and cant do important stuff without being root. :-?  \\:D/
Crap is child TERMINATED with 1 status.

---

### Post by cwaldbieser on 2005-08-21
[QUOTE=Linux_Noobie]Well yesterday i made the switch to ubuntu and plan on mainly using it after i get a internet on it (Using a labtop right now) so now i just need to know something..What is the root pass? I tried to do something in root but when i tried it just said.
 
So what does that mean o.0 I never set my root pass but used mandrake linux before and had it set but have no clue now and cant do important stuff without being root. :-?  \\:D/
Crap is child TERMINATED with 1 status.[/QUOTE]
Ubuntu does not have the root account activated by default.  Instead, the initial account you create can use "sudo" to get most jobs done.
For example:
```
$ sudo synaptic
``` 
will run the synaptic package manager with root powers.  When it asks for a password, you enter your user password.

---

