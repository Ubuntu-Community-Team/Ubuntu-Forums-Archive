---
title: "What environment am I running?"
date: 2007-05-13
forum: Desktop Environments
---

### Post by fatbuttlarry on 2007-05-13
I need a method to determine the Desktop Environment I'm running.

I checked ```
env
```

But it does not list anything related. :\

I don't mind parsing a file, but I can't find one!

I found the xsessions file that contains the default Environment, but that's not accurate, since the gdm splash can launch kde.

Any insight would be great!  Thanks!

-Tres

---

### Post by avb on 2007-05-13
from the terminal:

```
ps ax|grep gnome

```
if you get output -- u running gnome

```
ps ax|grep xfce 
```
if you get output -- u running xfce


```
ps ax|grep kdesktop

```
if you get output -- u running kde

---

### Post by fatbuttlarry on 2007-05-13
good thinking... 

This will be incorporated into a Java application, and it's rare I'll be able to query running applications without some native interface.  I'll check into that and get back.  In the mean time, any other suggestions are welcome!

-Tres

---

### Post by fatbuttlarry on 2007-05-13
This appears possible with the Java Runtime class.  Thanks for the advice.  I will be using it directly.  Although unrelated to Ubuntu, I'll try to post the java code that I end up using incase its asked again in the future.  link: [Runtime](http://java.sun.com/javase/6/docs/api/java/lang/Runtime.html) class

-Tres

---

