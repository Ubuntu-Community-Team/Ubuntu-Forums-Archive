---
title: "file permissions"
date: 2009-03-19
forum: General Help
---

### Post by terryq on 2009-03-19
I have a partiton on my slave drive (/dev/sdb1) which I use for my music mp3s. I am trying to rename some of the folders but root has ownership. Can anybody explain how I change the permissions.

---

### Post by s.fox on 2009-03-19
Hi,

[This]("https://help.ubuntu.com/community/FilePermissions") should be of great help to you.

-Ash R

---

### Post by fieroboom on 2009-03-19
Well, I normally would want more information before I start tossing out permissions commands, but you're asking for them directly... :)
```
sudo chown username:username /mountpoint
```
Just be *very* sure that you perform that command on the *correct* directory. In the wrong directory, it'll cripple your system.
:D
-Paul

---

### Post by terryq on 2009-03-19
Thank you so much for the quick replies...appreciated!!!

---

### Post by jlochhead on 2009-03-19
Shouldn't you be doing that recursively?

- Mount your drive.

- cd /path/to/your/drive

- sudo chown -R <yourusername> *

---

### Post by jlochhead on 2009-03-19
NVM, it obviously worked.

---

