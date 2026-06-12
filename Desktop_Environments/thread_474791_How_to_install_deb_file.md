---
title: "How to install deb file"
date: 2007-06-15
forum: Desktop Environments
---

### Post by yinglcs2 on 2007-06-15
Hi,

i am trying to install a 'deb' file, but it keep saying it can't find ' package skype-1.4.0.74.deb'.
Can you please help me?

$ sudo apt-get install skype-1.4.0.74.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype-1.4.0.74.deb

$ ls -la skype-1.4.0.74.deb 
-rw-r--r-- 1 yinglcs yinglcs 11281722 2007-06-15 09:39 skype-1.4.0.74.deb

---

### Post by scrooge_74 on 2007-06-15
Go to skype website and get the repository for it and then you can install it

---

### Post by yinglcs2 on 2007-06-15
I did download 'skype-1.4.0.74.deb' from skype web site.

i just don't know how to install it from the file.

Thank you for any help.

---

### Post by Phixion on 2007-06-15
Hate to say this but... google is your friend! :D

dpkg -i file.deb

---

### Post by FuturePilot on 2007-06-15
You could just double click it and let Gdebi take care of it.

---

### Post by RedSquirrel on 2007-06-15
> **yinglcs2 said:**
> I did download 'skype-1.4.0.74.deb' from skype web site.

i just don't know how to install it from the file.

Thank you for any help.

Install it with this:

```
sudo dpkg -i skype-1.4.0.74.deb
```

---

