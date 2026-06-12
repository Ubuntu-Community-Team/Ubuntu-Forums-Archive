---
title: "how do you check your driver?"
date: 2009-01-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wolfyking2 on 2009-01-14
how do you check your graphical driver (or whatever you call it)  Because I wanna upgrade it soon so Savage 2 will play better :)
y'know, the drivers like nVidia or ATI

---

### Post by wolfyking2 on 2009-01-14
help?:mad:

---

### Post by Titan8990 on 2009-01-14
System -> Administration -> Restricted Hardware Manager 


Or:


gksu jockey-gtk

---

### Post by wolfyking2 on 2009-01-14
There's nothing in there...

---

### Post by Neumy on 2009-01-14
Try: **lspci -nn | grep VGA**

If you're installing video drivers, here's two links for you to check out.

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by linux_tech on 2009-01-15
To find out more detailed info about video driver, in a terminal type:
```
cat /var/log/Xorg.0.log 
```

---

