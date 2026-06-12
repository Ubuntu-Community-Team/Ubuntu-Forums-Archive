---
title: "Permission denied..."
date: 2008-12-14
forum: General Help
---

### Post by Shiv4m on 2008-12-14
I was trying to install the new GIMP update and I get this error:

[IMG]http://img67.imageshack.us/my.php?image=screenshotshivamshivamlby4.png[/IMG]
[[IMG]http://img67.imageshack.us/img67/6360/screenshotshivamshivamlby4.png[/IMG]](http://imageshack.us)
[[IMG]http://img67.imageshack.us/img67/screenshotshivamshivamlby4.png/1/w659.png[/IMG]](http://g.imageshack.us/img67/screenshotshivamshivamlby4.png/1/)

I want to know how to become root..

Thanks in advance

---

### Post by cariboo on 2008-12-14
You need to prepend your command with sudo eg:

```
sudo apt-get install gimp
```

When installing programs, you need to be root, as your regular user can only write files to your home directory. 

This is also the reason why linux malware has a hard time propagating, as unless you install it as root, it isn't going to work.

Jim

---

### Post by eBoxNet on 2008-12-14
sudo apt-get install ...

---

### Post by Shiv4m on 2008-12-14
Lol how embarassing :) +1 for both!

---

