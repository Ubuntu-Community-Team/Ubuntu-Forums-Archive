---
title: "I cannot change my password"
date: 2012-04-21
forum: Desktop Environments
---

### Post by forsubhi on 2012-04-21
```
subhi@subhi-pc:~$ passwd 
Changing password for subhi.
(current) UNIX password: 
passwd: Module is unknown
passwd: password unchanged
```

what is the problem ?

---

### Post by dniMretsaM on 2012-04-21
That would indicate something is messed up with PAM. Try this:
```
sudo pam-auth-update --force
```

---

### Post by forsubhi on 2012-04-22
no thing happened after 

sudo pam-auth-update --force 

 		                   		  		  		  		  		  	 I am using kubuntu 11.10

---

