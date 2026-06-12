---
title: "Need a command to count installed packages"
date: 2009-05-24
forum: General Help
---

### Post by colau on 2009-05-24
Hi,
Is there any command to know how many packages are installed in ubuntu 9.04?

---

### Post by benson444 on 2009-05-24
I think

```
dpkg --list | wc -l
```

---

### Post by colau on 2009-05-24
> **benson444 said:**
> I think

```
dpkg --list | wc -l
```
Thanks.

---

### Post by hrabbit on 2009-11-14
> **benson444 said:**
> I think

```
dpkg --list | wc -l
```


I know this thread is old but the result you are getting is actually wrong. This will also list removed packagaes as well.

Try something closer to

```
dpkg -l |grep ^ii | wc -l
```

---

