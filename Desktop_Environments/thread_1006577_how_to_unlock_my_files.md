---
title: "how to unlock my files"
date: 2008-12-09
forum: Desktop Environments
---

### Post by shogunmidas on 2008-12-09
i am moving my files from some data dvd's and when i put them on my desktop they are all locked and i have to change the permissions for each individual file. is there any way where i can set it up to automatically allow me read and write privileges to all new files?

---

### Post by taurus on 2008-12-09
You can change all of them, assuming they are all in the same directory, with chmod from a terminal.  When you copy files over from the DVD, they keep their original permissions so you need to change them to whatever you want once they are on your $HOME.

---

### Post by shogunmidas on 2008-12-09
thank you kind sir. that respons was pretty damn fast! 

but im brand new to anything linux... what is chmod and how do i use it?

---

### Post by taurus on 2008-12-09
```
man chmod
```
Where did you move those data files?  Did you copy them to your ~/Desktop?

```
ls -la ~/Desktop
```

---

