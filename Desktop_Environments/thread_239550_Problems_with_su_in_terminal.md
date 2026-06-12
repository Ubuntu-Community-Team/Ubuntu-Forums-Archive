---
title: "Problems with su in terminal"
date: 2006-08-19
forum: Desktop Environments
---

### Post by fatsheep on 2006-08-19
When I try to use su in the terminal I get an authorization error:

> 
fatsheep@fatsheep:~$ su
Password:
su: Authentication failure
Sorry.


I've tried many times and I'm 100% sure I'm typing my password in correctly.  Is there a bug in the terminal or something? :confused:

---

### Post by Dr. Nick on 2006-08-19
Ubuntu doesnt use root by default, to launch a command as rood use [B]sudo

[/B]to get a root terminal use[B] sudo su

[http://www.psychocats.net/ubuntu/sudo.php](http://www.psychocats.net/ubuntu/sudo.php)
[/B]

---

### Post by fatsheep on 2006-08-19
Ah thank you, I forgot that Ubuntu uses sudo instead of su.  My bad ... :(

---

### Post by PathSpace on 2006-08-19
You can enable root user.  Go to System->Administration->Users and Groups.  Then click the place which says "Show all users and groups."  Then you can change the root password if you want.

---

