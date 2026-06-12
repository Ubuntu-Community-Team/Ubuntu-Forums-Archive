---
title: "gksu/gksudo security?"
date: 2006-06-25
forum: Desktop Environments
---

### Post by bobgreen5s on 2006-06-25
I noticed that when I ran one application such as synaptic package manager I was prompted for a password. After I closed synaptic package manager I ran gksu network-admin and I was not prompted for a password. So it seems to me that gksu lasts for the entire session meaning you are only prompted for the password once each session. My question is, is it possible to make gksu more secure where the user is prompted for his password each times he runs the application (without using the command line sudo), ex: user runs application a and is prompted for his password then user runs application b and is once again prompted for his password.

---

### Post by aysiu on 2006-06-25
It doesn't last the entire session. It lasts 15 minutes--same for *sudo* or *kdesu*.

[This post](http://ubuntuforums.org/showpost.php?p=116697&postcount=6) will tell you how to change the timeout.

---

### Post by bobgreen5s on 2006-06-25
ah thanks that was exactly what I was looking for :)

---

