---
title: "saving file permission denied"
date: 2009-06-12
forum: General Help
---

### Post by sciencegirl on 2009-06-12
Hello!

I am trying to save a file to /usr/local/bin using a software program called Edgewarp. When I try to do this I get a permission denied message.
I know how to use sudo or login as root when dealing with files from within the terminal. How do I save a file from within a software package? 

Thank You!!

---

### Post by LowSky on 2009-06-12
save the file to the desktop forst then ope a temrinal

```
gksu nautilus
```

now copy the file to the directory required close nautilus and your all set

---

### Post by sciencegirl on 2009-06-12
cool thanks i'll try that!

---

### Post by sciencegirl on 2009-06-12
It worked! Thanks!

---

### Post by wgelnaw on 2011-01-17
I just downloaded Edgewarp but can't get it working at all.  In my case, when I try to click on the box to allow the file to run as an executable, it won't allow it.  Did you run into anything similar?  I tried "\edgewarp-3.30\bin\ sudo chmod +x ewsh" in terminal, but that didn't do anything.  Any suggestions?

---

### Post by vidtek on 2011-01-17
> **LowSky said:**
> save the file to the desktop forst then ope a temrinal

```
gksu nautilus
```

now copy the file to the directory required close nautilus and your all set

LowSky--Just a little query, how do you do this in a KDE4 ubuntu system?

Tony.

---

