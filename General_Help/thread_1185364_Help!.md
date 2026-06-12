---
title: "Help!"
date: 2009-06-12
forum: General Help
---

### Post by sophie martin on 2009-06-12
Have just downloaded Ubuntu, put in username and password as part of setup and have obviously made a typo error as I now cannot sign in. How do I change both so I can get into Ubuntu?:(

---

### Post by t0p on 2009-06-12
If you boot your computer holding down the Escape key, you should be brought to a menu that consists of a list of available kernels, a memtest, and a recovery mode.  If you select this recovery mode, you will be logged into a root shell without having to provide your password first.  Then you should be able to give the command

```
passwd
```

and this will let you change your password without having to type the old one first.

---

