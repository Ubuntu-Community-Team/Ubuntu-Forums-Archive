---
title: "Synaptic Package Manager error"
date: 2009-02-08
forum: General Help
---

### Post by tompask on 2009-02-08
Hi i am new to the whole linux based operating systems i am trying to install a program so i tried to acces the Synaptic Package Manager and keep getting an error:

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to  correct the problem. 
E: _cache->open() failed, please report.

I have also tried to add it manually but as i said newbie here!

I would appreciate any help you could give me!
Thanks

---

### Post by howefield on 2009-02-08
Open a terminal, (Applications > accessories > terminal) and type
```

sudo dpkg --configure -a
```

It will ask for your password, type it in and you should be good.

---

### Post by Tim Sharitt on 2009-02-08
Open a terminal (Applications > Accessories > Terminal) and run
```
sudo dpkg --configure -a
```

---

### Post by tehforum on 2009-02-08
[Have a look.]("http://ubuntuforums.org/showthread.php?t=388348")

---

