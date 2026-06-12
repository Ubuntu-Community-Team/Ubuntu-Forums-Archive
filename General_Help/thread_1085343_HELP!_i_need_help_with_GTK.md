---
title: "HELP! i need help with GTK"
date: 2009-03-02
forum: General Help
---

### Post by 220010497 on 2009-03-02
heloo, helpfuly i need help with GTK2,   well i've been looking thru fourms becase i get an annyoing message saying "this theme will not fully be applyed becase GTK2 is not installed"    

so can some one help this is what i put in:
husky@husky-laptop:~$ apt-get install libgtk1.2-dev
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


i dont under stand what its saying. i'm a bit of a new user, i've used Ubuntu for about a month. and i....LOVE IT!!!! hehehe, well i love themes though, so plz help

---

### Post by handy on 2009-03-03
Are you running Privoxy?

---

### Post by DirtDawg on 2009-03-03
> **220010497 said:**
> heloo, helpfuly i need help with GTK2,   well i've been looking thru fourms becase i get an annyoing message saying "this theme will not fully be applyed becase GTK2 is not installed"    

so can some one help this is what i put in:
husky@husky-laptop:~$ apt-get install libgtk1.2-dev
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


i dont under stand what its saying. i'm a bit of a new user, i've used Ubuntu for about a month. and i....LOVE IT!!!! hehehe, well i love themes though, so plz help

I'm not sure if installing the libgtk1.2-dev package will solve your overall problem, but when you tried to install it, you forgot the 'sudo' part of the command (hence the errors about permission). Try
```
sudo apt-get install libgtk1.2-dev
```

---

