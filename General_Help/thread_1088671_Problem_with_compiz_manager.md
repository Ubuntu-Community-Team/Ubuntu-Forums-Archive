---
title: "Problem with compiz manager"
date: 2009-03-06
forum: General Help
---

### Post by PwnCakes193 on 2009-03-06
When I go to the Windows section in preferences, I get the following message:
Window manager "compiz" has not registered a configuration tool

I am running Ubuntu 9.04 alpha 5 if that makes any difference.

---

### Post by Roanoke on 2009-03-06
Try running this:
```

sudo apt-get install ccsm

```

---

### Post by PwnCakes193 on 2009-03-07
> **Roanoke said:**
> Try running this:
```

sudo apt-get install ccsm

```

I get this....

tom@tom-laptop:~$ sudo apt-get install ccsm
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm
tom@tom-laptop:~$

---

### Post by Roanoke on 2009-03-08
```

apt-get install simple-ccsm

```

---

