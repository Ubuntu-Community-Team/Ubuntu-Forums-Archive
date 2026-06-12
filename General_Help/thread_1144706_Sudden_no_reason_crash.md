---
title: "Sudden no reason crash"
date: 2009-05-01
forum: General Help
---

### Post by Ravernomina on 2009-05-01
hello... I was using Ubuntu and for no reason just a giant freeze up nothing was working not even my mouse.... I then cold booted and got back into ubuntu everything seems fine, i went through the logs and nothing really seems like a root kit... and i also did a root kit scans as well... if some 1 can be kind enough to tell me house to use fsck command correctly to make sure my FS is ok that would be great TYVM!!!.


P.s. attached is my kernel Log, daemon log, and auth log. please take a look if u want and mabe see what went wrong.

---

### Post by Ravernomina on 2009-05-01
Bump

---

### Post by Bucky Ball on 2009-05-01
If it happens again, you could drop to a terminal straight away (ctl/alt/F1) and type:

```
dmesg
```

What are the errors it is throwing toward the end of the list, the last few events?

---

### Post by codeseer on 2009-05-01
Join the group: [http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

---

### Post by Ravernomina on 2009-05-01
when i was looking it was something with IP address look at the logs for more info.

---

### Post by Ravernomina on 2009-05-01
Bump

---

### Post by codeseer on 2009-05-01
> **Ravernomina said:**
> when i was looking it was something with IP address look at the logs for more info.

Yeah, many have complained about crashes coming in Jaunty when they are performing network activities as well. The best thing you can do at this point, at least that I know of, is to upgrade the kernel.

---

### Post by Bucky Ball on 2009-05-01
Or even update, that also seems to be working for some:

```
sudo apt-get update
```

... in a terminal.

---

