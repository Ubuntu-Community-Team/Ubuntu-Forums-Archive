---
title: "Change user"
date: 2006-06-07
forum: Desktop Environments
---

### Post by risager on 2006-06-07
I've installed a program called slimserver which apparently created a user called slimserver (which seems to have no password??) that is used for running the program. 

To do some debugging I would like to have a shell where I can run apps as this user. I tried  "su slimserver", which asks for a password I do not have, and "sudo su slimserver"  

Suggestions?

---

### Post by Ramses de Norre on 2006-06-07
```
sudo passwd slimserver
```

---

### Post by risager on 2006-06-07
I tried that. But I can still cannot become this new user:
```
morten@toshiba:~$ sudo passwd slimserver
Password:
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
morten@toshiba:~$ su slimserver
Password:
morten@toshiba:~$ whoami
morten

```

---

