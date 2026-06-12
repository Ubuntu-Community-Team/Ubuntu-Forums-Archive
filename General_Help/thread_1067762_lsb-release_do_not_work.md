---
title: "lsb-release do not work"
date: 2009-02-12
forum: General Help
---

### Post by dox_drum on 2009-02-12
Hi there!

Playing around with the xterm, I've noted that the command line ``lsb_release'' isn't working any more.

```

oscar@dell-desktop:~$ lsb_release 
No LSB modules are available.

```

Any ideas of what's going on?!


Thank you.

[CENTER]Enjoy![/CENTER]

---

### Post by drs305 on 2009-02-12
That is a normal response for my machine. Try:
```
lsb_release -a
```
for version/code name information. 

(Unless the problem is your output previously included LSB module information in the past and now it doesn't.)

---

### Post by kostkon on 2009-02-12
What do you get if you give
```
lsb_release -a
```

---

### Post by Kevbert on 2009-02-12
Try
```
lsb_release -a
```
That works but still gives the same error.
The alternative is to use
```
uname -a
```

---

### Post by dox_drum on 2009-02-12
That's right!!! 

It worked.

Thank you all.

---

