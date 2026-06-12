---
title: "How can I check which application is consuming bandwidth?"
date: 2012-06-14
forum: Desktop Environments
---

### Post by prismctg on 2012-06-14
How can I check which application is consuming bandwidth?

---

### Post by Frogs Hair on 2012-06-14
Start by reviewing what applications that connect to the net automatically. File sync programs like Ubuntu one will connect automatically. If you use Rhythmbox or other media players make sure you have quit the application no just closed it. I use last .fm and it will remain connected unless I quit Rhythmbox.

---

### Post by Morbius1 on 2012-06-14
See if nethogs does what you want:
```
sudo apt-get install nethogs
```Then in a terminal run:
```
sudo nethogs
```

---

### Post by dixoncx on 2012-06-15
Thanks Morbins :)
I was looking for one like this for a long time...
[]("http://ubuntuforums.org/member.php?u=982144")

---

### Post by prismctg on 2012-06-16
Thanx Morbius1  ; Nethogs is a great tool

---

