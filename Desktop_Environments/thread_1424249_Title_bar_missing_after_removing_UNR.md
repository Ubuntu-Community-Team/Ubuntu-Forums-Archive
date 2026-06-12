---
title: "Title bar missing after removing UNR"
date: 2010-03-07
forum: Desktop Environments
---

### Post by c1tlr340 on 2010-03-07
Hi All,

I have an Asus 1201n netbook, thought I would try netbook remix by install packages from repositories.

UNR was not for me so I uninstalled it.

Now my title bars have gone, close, minimize and maximize gone. Screenshot attached.

How do I get them back.

---

### Post by Ultra_Man on 2010-03-07
try going to compiz config and enabling window decoration.

---

### Post by c1tlr340 on 2010-03-07
Thanks for the quick reply, I haven't installed compiz.

---

### Post by mister_playboy on 2010-03-07
Maximus is installed with UNR, but is not uninstalled with it... this should fix your problem:

```
sudo apt-get remove maximus
```

You will then need to logout and back in.

---

### Post by c1tlr340 on 2010-03-08
> **mister_playboy said:**
> Maximus is installed with UNR, but is not uninstalled with it... this should fix your problem:

```
sudo apt-get remove maximus
```

You will then need to logout and back in.

Thanks mister_playboy, this solved my problem.:D

---

### Post by mister_playboy on 2010-03-09
> **c1tlr340 said:**
> Thanks mister_playboy, this solved my problem.:D

I had the exact same issue as you did when I installed and then uninstalled UNR a few months ago... had to come here and ask for help.

You learn and pass it on to the next person. ;)

---

