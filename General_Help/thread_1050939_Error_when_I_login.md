---
title: "Error when I login"
date: 2009-01-26
forum: General Help
---

### Post by supanatral on 2009-01-26
Whenever I log into my ubuntu server, I will get this:

> login as: administrator
Using keyboard-interactive authentication.
Password:
Error
Last login: Mon Jan 26 08:31:10 2009 from ibm-p4e.local
administrator@ubuntu:~$ su
Password:
Error
root@ubuntu:/home/administrator#


As you also see above, even when I 'su' into root, it gives me that error. why is that?

---

### Post by Kevbert on 2009-01-26
What do you get if you use
```
sudo su
```
?

---

### Post by supanatral on 2009-01-26
> **Kevbert said:**
> What do you get if you use
```
sudo su
```
?

Here is what I get:
> administrator@ubuntu:~$ sudo su
[sudo] password for administrator:
Error
root@ubuntu:/home/administrator#

---

### Post by amauk on 2009-01-26
you may want to see if there's anything in
/var/log/auth.log
or
/var/log/messages
regarding the error
(it's a bit odd that it just says "error" without giving some kind of explanation)

---

