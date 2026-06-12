---
title: "sudo: /var/lib/sudo owned by uid XXX, should be uid 0"
date: 2011-11-23
forum: Desktop Environments
---

### Post by jamiehutber on 2011-11-23
So its simple whenever i try to use sudo i get this error:
> sudo: /var/lib/sudo owned by uid 337784488, should be uid 0
I have been getting this for some weeks without any problem other than it flashing up each time i tried to use sudo.

As of today my clock had re-set, i can not install any packages where it asks to me to authenticate. I get this error when they ask 'Password for root:':
> Your authentication attempt was unsuccessful. Please try again.
Also all https certificates require  me to confirm the acceptance, where i never got this dialog box.

Now i haven't changed my password. Last night my laptop ran out of battery and upon booting up it did a hard drive check. Interestingly if i use something like synaptic package manager > Enter your administrator password to perform tasks i get no problem with the same password.

Also 2 days ago i had to add myself to visudo file as hutber ALL=(ALL:ALL) ALL. Not sure if these things are linked :/

---

### Post by jamiehutber on 2011-11-24
bump?:(

---

### Post by typhoon_tip on 2011-11-24
Just google it, and found this:
[http://kubuntuforums.net/forums/index.php?topic=3097130.0](http://kubuntuforums.net/forums/index.php?topic=3097130.0)

Can you try to do this for test:
```
gksudo apt-get update
```

If it works, do not use sudo anymore, just use gksudo.

---

