---
title: "How to uninstall MYSQMAIL"
date: 2010-05-24
forum: Desktop Environments
---

### Post by bovcan on 2010-05-24
Hello!
One time mysqmail was installed becouse of dependecies and at the end some error happen.
Now, everytime I want to install something this happen
> E: mysqmail: subprocess installed post-installation script returned error exit status 10
E: mysqmail-dovecot-logger: dependency problems - leaving unconfigured


In Synaptic PM I tried to remove mysqmail but I can't.I recive this error:> 
E: mysqmail: subprocess installed pre-removal script returned error exit status 1


Any idea how to remove this?

Using Ubuntu 10.04

Regards

---

### Post by bovcan on 2010-05-24
bump

---

### Post by bovcan on 2010-05-26
bump

---

### Post by bovcan on 2010-05-30
Still do not know how to delete this.

---

### Post by bovcan on 2010-06-02
Ok, finaly I remove this crap from PC.
I went to usr/share/doc and delete mysqmail folder
than I run Synaptic Package Maneger and click to remove mysqmail. Now it remove without any issue.

---

### Post by sigtechauto on 2010-08-15
Hello,

Regarding this uninstalling mysqmail I did as described below,

> **bovcan said:**
> Ok, finaly I remove this crap from PC.
I went to usr/share/doc and delete mysqmail folder
than I run Synaptic Package Maneger and click to remove mysqmail. Now it remove without any issue.
 
to no avail.  I chose complete removal in Synaptic and received this answer,

E: mysqmail: subprocess installed pre-removal script returned error exit status 1

How to solve it please?

Thanks in advance,

Andre Luiz

---

### Post by sigtechauto on 2010-08-17
Hello,

I found the answer (from a friend actually),

apt-cache search mysqlmail
apt-cache search mysql | grep mail
apt-get remove --purge mysqmail

Best,

Andre

---

