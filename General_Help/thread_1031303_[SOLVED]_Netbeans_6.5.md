---
title: "[SOLVED] Netbeans 6.5"
date: 2009-01-05
forum: General Help
---

### Post by Jelmoh on 2009-01-05
Respected Ubuntu forum members!

I really need your help!

I've got netbeans 6.5 installed and so forth!

But.. The problem is that the main dir for projects is another dir than the localhost dir of Apache2 (which is /var/www in my case).
So, in Netbeans it's possible to copy the project to another location, but when I try that it says that it isn't allowed to create a folder on that location (any location for that matter).

I think I can solve the problem by opening Netbeans 6.5 as root (which isn't wise I know..).
My real problem is I can't open Netbeans as root in terminal..
I've tried several commands like:
```
sudo netbeans
sudo netbeans-6.5
```
etc etc..
I even tried copying the main executable into the terminal..

Many thanks in advance!

---

### Post by Jelmoh on 2009-01-07
Solved the problem myself.. :)
Changed the permissions of the /var/www directory..
It can't be done normally so I used the following command:
```
sudo nautilus
```
It can probably be done with the normal chmod commands.. :)

---

