---
title: "Server install"
date: 2006-05-05
forum: Desktop Environments
---

### Post by JBL on 2006-05-05
I did a server install...Now how do i get fluxbox on here?

---

### Post by Sef on 2006-05-05
To install fluxbox, read this doc.

[http://doc.gwos.org/index.php/FluxboxSource]("http://doc.gwos.org/index.php/FluxboxSource")

---

### Post by JBL on 2006-05-05
I did a server install and when i try "sudo apt-get install fluxbox x-window-system-core xdm synaptic," i get an error saying it can not find "x-window-system-core."

---

### Post by JBL on 2006-05-05
?

---

### Post by Sutekh on 2006-05-05
Check to see if your sources.list contains the security repository
```
cat /etc/apt/sources.list
```
You should have these two lines
```
deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted

```

---

### Post by JBL on 2006-05-05
It does have them two lines but it still can't find 'x-window-system-core' or 'x-window-system'

---

### Post by JBL on 2006-05-05
Anyone?

---

### Post by Sutekh on 2006-05-05
I don't really know how to diagnose this problem.

What happens if you refresh the source package lists
```
sudo apt-get update
sudo apt-get install fluxbox x-window-system-core xdm synaptic
```
I'll boot into Breezy to see if I have this problem too.

---

### Post by JBL on 2006-05-05
Already updated it. Still no luck.

---

### Post by Sutekh on 2006-05-05
What are the contents of your sources.list?  Are they using local repositories?  Like
```
deb http://**us.**archive.ubuntu.com/ubuntu breezy main restricted
```
If so try removing the **us.** (or whatever) part of the repositories and then try the update and install commands again.

---

### Post by JBL on 2006-05-06
*Fixed

---

### Post by Sutekh on 2006-05-06
Do tell.  What was the problem in the end?

---

