---
title: "need help interrupted dpkg"
date: 2009-03-03
forum: General Help
---

### Post by raymondh on 2009-03-03
I was installing azureus thru the terminal when we lost AC power.  On reboot and trying to continue installation, I get a message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report

Not knowing anything, I  tried alt+F2 for the command box and typed in exact wordings/space without the '.  System is hanging.:(

Need help ...what should I do to correct this problem? .... am new to ubuntu and linux (in general)

Thanks in advance

---

### Post by taurus on 2009-03-03
```
sudo dpkg --configure -a
```

---

### Post by raymondh on 2009-03-03
Thanks taurus .... "muchas gracias" as speedy gonzalez would say:D

---

