---
title: "make command not found"
date: 2005-11-14
forum: Desktop Environments
---

### Post by AllenP on 2005-11-14
Why does it tell me that it cant find the make command when I try to install airsnort? I tried "Sudo make" but that didnt work either. Help would be appreciated. I've been using linux for around 2 months.

---

### Post by 23meg on 2005-11-14
```
sudo apt-get install make
``` should help.

---

### Post by ssam on 2005-11-14
do you really need to build this from source? is it not in any of the repositories?

you might need more than just make if you do want to build it.

```
sudo apt-get install build-essential
```

---

### Post by bartc on 2005-11-14
[QUOTE=ssam]do you really need to build this from source? is it not in any of the repositories?[/QUOTE]
Yes, it is:```
sudo apt-get install airsnort
```

---

### Post by elreteipos on 2005-11-19
How can you install make without having to use internet? (my internet doesn't work on Linux)

---

