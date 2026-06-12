---
title: "ssh"
date: 2009-01-18
forum: Desktop Environments
---

### Post by num on 2009-01-18
i install SSH on my ubuntu box 192.168.1.3 is the internal ip address but whenever i try to login as "root" with a valid password it says "access denied". what's going on?

---

### Post by CLomax on 2009-01-18
Either you're getting your root password wrong or the target computer has port 22 closed.

Btw, wrong section :P

---

### Post by binbash on 2009-01-18
check your sshd config if root login allowed or not

---

### Post by num on 2009-01-18
how can i check sshd config?

---

### Post by apmcd47 on 2009-01-18
> **num said:**
> how can i check sshd config?

Look in /etc/ssh and read the file sshd_config.

Andrew

---

### Post by blackened on 2009-01-18
> **num said:**
> how can i check sshd config?

Open /etc/ssh/sshd_config with your favourite text editor and go to town.

**Edit:** Oops, too slow.

---

### Post by ac7ss on 2009-01-18
Ubuntu won't allow a root login by default. Login as an user with adm group access and then you can *sudo* your root commands. (or *sudo su*)

---

