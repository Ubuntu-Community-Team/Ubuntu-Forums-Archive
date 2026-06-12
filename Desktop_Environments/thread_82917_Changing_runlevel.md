---
title: "Changing runlevel"
date: 2005-10-27
forum: Desktop Environments
---

### Post by savageisland on 2005-10-27
How do I change Ubuntu so it starts up with run level 3?

---

### Post by Pygi on 2005-10-27
Please reffer to this topic for your solution:

[http://ubuntuforums.org/showthread.php?p=188161](http://ubuntuforums.org/showthread.php?p=188161)

---

### Post by kabus on 2005-10-27
You can change it in /etc/inittab :

```
# The default runlevel.
id:3:initdefault:
```

---

