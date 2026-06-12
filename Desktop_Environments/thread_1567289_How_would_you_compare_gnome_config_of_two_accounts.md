---
title: "How would you compare gnome config of two accounts on the same system ?"
date: 2010-09-03
forum: Desktop Environments
---

### Post by JackD on 2010-09-03
In troubleshooting intermittent problems with an application, it works fine with a different account on the same system. 

- The rights are identical between accounts
- It looks as though there is a desktop difference, but I can't see it. 
- I can't load gconf-editor twice (under different account names).
- And, I can't simply print out all the gnome configuration information for each account (that would be nice).

I'm stuck and I'm pretty confident that there is straightforward way to compare gnome settings on the same system.

One, rather draconian, option is to wipe out all gnome settings:

   rm -rf .gnome .gnome2 .gconf .gconfd .metacity

This is quite a broad brush, when I'm sure that the misconfiguration is something small.

But, how to find it ?

---

