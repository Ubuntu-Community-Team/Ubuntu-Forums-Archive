---
title: "Stuck booting to console after switch from kdm to gdm"
date: 2007-11-12
forum: Desktop Environments
---

### Post by frkstein on 2007-11-12
I recently switched from kdm to gdm. Now, when ever I boot my machine I am dumped to the console instead of the login environment of gdm.  I can login a user and then do sudo gdm to get the graphical login back. I have tried sudo dpkg-reconfigure gdm, but no luck. Any suggestions?

---

### Post by taurus on 2007-11-12
Do you have a copy of gdm in /etc/init.d?

```
ls -la /etc/init.d/gdm
```

---

### Post by frkstein on 2007-11-12
Yes, I do have a copy of gdm in located in /etc/init.d

---

### Post by taurus on 2007-11-12
Maybe you want to look in System -> Administration -> Services to be sure you have gdm started at boot.

---

### Post by frkstein on 2007-11-12
That did it! Thank you very much!

---

