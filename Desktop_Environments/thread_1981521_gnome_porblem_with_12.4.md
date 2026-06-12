---
title: "gnome porblem with 12.4"
date: 2012-05-16
forum: Desktop Environments
---

### Post by abdorefky on 2012-05-16
after i updated ubuntu 11.10 to 12.4 ,, system testing is forcing 
system to log out and some other things do such things :
latest problem : i can't install gnome 
[IMG]http://img215.imageshack.us/img215/560/screenshotfrom201205170.png[/IMG]
[SIZE="3"]BTW system testing still crashing my system :
i hope to know if there is any diagnose tool for gnome or the ubuntu system files [/SIZE]

---

### Post by abdorefky on 2012-05-23
I am the only one who have this problem ?

---

### Post by abdorefky on 2012-06-05
hmmm

---

### Post by coffeecat on 2012-06-05
> **abdorefky said:**
> after i updated ubuntu 11.10 to 12.4 ,, system testing is forcing 
system to log out and some other things do such things :
latest problem : i can't install gnome 

If you originally installed Ubuntu (rather than Kubuntu, Xubuntu or Lubuntu) you already have gnome. The problem in your screenshot indicates a dependency one. There is probably a problem with your sources. Please open a terminal and post the output of these two commands:

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

You can paste the output into your post by highlighting it with the mouse and right-click -> copy. The first command will produce quite a lot of text so please be sure to copy and paste all of it.

---

