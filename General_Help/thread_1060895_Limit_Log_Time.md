---
title: "Limit Log Time"
date: 2009-02-05
forum: General Help
---

### Post by echo8413 on 2009-02-05
I'm trying to limit the amount of time a user can be on my ubuntu system at my house. I've been finding various commands that are not even in the manual such as:

logoutd
porttime
timeoutd
timekpr

Is there any real commands that will allow to limit a user's logon time.

---

### Post by dcstar on 2009-02-05
> **echo8413 said:**
> I'm trying to limit the amount of time a user can be on my ubuntu system at my house. I've been finding various commands that are not even in the manual such as:

logoutd
porttime
**timeoutd**
timekpr

Is there any real commands that will allow to limit a user's logon time.

[http://pwet.fr/man/linux/administration_systeme/timeoutd](http://pwet.fr/man/linux/administration_systeme/timeoutd)

---

### Post by wirelessmonkey on 2009-02-05
You do need to install these applications if you wish to use them....
```

sudo apt-get install timeoutd

```
for instance

---

