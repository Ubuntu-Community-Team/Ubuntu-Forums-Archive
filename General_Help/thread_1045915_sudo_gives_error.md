---
title: "sudo gives error"
date: 2009-01-20
forum: General Help
---

### Post by PoopyTheJ on 2009-01-20
Whenever I use sudo for a command I get an erro thrown up, at least I think it's an error, it says...

sudo: unable to resolve host username-desktop

Anyone know why this occurs?

Running Hardy, Thanks!

---

### Post by dcstar on 2009-01-20
> **PoopyTheJ said:**
> Whenever I use sudo for a command I get an erro thrown up, at least I think it's an error, it says...

sudo: unable to resolve host username-desktop

Anyone know why this occurs?

Running Hardy, Thanks!

You do not have correct entries in your /etc/hosts file or /etc/hostname.

---

### Post by DeMus on 2009-01-20
> **PoopyTheJ said:**
> Whenever I use sudo for a command I get an erro thrown up, at least I think it's an error, it says...

sudo: unable to resolve host username-desktop

Anyone know why this occurs?

Running Hardy, Thanks!

In my /etc/hostname file it only says the name of my computer. That's all. Just: 2-quad
No more, no less.
What's in your file?

---

### Post by adult swim on 2009-01-20
paste what ```
cat /etc/hosts
``` returns

---

### Post by zvacet on 2009-01-21
Boot in recovery mode and type

```
nano /etc/hosts
```

and first two lines shoiuld look like this

127.0.0.1 localhost
127.0.1.1 **your_computer_name**

Make changes and save and exit file.Restart and you should be fine.

---

### Post by PoopyTheJ on 2009-01-21
Thank you, I had my computername.workgroup getting rid of .workgroup fixed the error

---

