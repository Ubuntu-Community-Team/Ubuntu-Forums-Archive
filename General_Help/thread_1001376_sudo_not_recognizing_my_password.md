---
title: "sudo not recognizing my password"
date: 2008-12-03
forum: General Help
---

### Post by el_itur on 2008-12-03
it happens only in the terminal. whenever I want to run some command as sudo it asks me for my password which I enter correctly three times only to be rejected.

The pass works fine in the gui (synaptic, keyring, etc)

just odd... Some one have any pointer?

I'm using intrepid BTW

---

### Post by sedawk on 2008-12-03
May be the keyboard mapping in the terminal is different from
the GUI mapping.
Enter the password in the terminal so you can see it
and as username when logging in (without pressing return
afterwards, but delete the characters again with backspace).
Any difference - e.g. the famous y <-> z swapping ?

---

### Post by linux_tech on 2008-12-03
Boot in recovery mode
add user username to the admin group so you can sudo 
```
adduser username admin
```
instructions:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

