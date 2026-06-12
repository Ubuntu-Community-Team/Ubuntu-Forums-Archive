---
title: "Synaptics package manager error! Please Help!"
date: 2009-04-23
forum: General Help
---

### Post by Quantum Fabric on 2009-04-23
Ok, so I'm somewhat familiar with ubuntu, but not too much. 

When using the package manager to try to get a file it froze and I had to restart, upon trying to reopen it I got this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to look on the terminal for the dpkg and look through the help, but I'm not super savy with the terminal.

I understand I can get all my stuff with gedit, but I would really prefer to use the synaptics one. 

Any help would be amazing!!!

---

### Post by Tim Sharitt on 2009-04-23
Open a terminal (Applications > Accessories > Terminal) and enter:
```
sudo dpkg --configure -a
``` 

You will then need to enter your password when prompted.

If it gives you any errors, post them here.

---

