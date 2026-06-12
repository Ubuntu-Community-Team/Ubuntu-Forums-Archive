---
title: "VMWare problem"
date: 2005-12-17
forum: Desktop Environments
---

### Post by dvejnovic on 2005-12-17
I have KUbuntu 5.10. I can run VMWare workstation as root or as user with sudo rights. If I want to run program as normal user, I get the following error:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

What's wrong?:???:

---

### Post by MartinG on 2005-12-17
Sounds a bit unlikely, but I wonder if you installed from a root login, rather than using sudo in a terminal?

---

### Post by dvejnovic on 2005-12-17
[QUOTE=MartinG]Sounds a bit unlikely, but I wonder if you installed from a root login, rather than using sudo in a terminal?[/QUOTE]

I installed it using sudo...

---

### Post by MartinG on 2005-12-17
I sometimes get it the other way round, where I can't start an X app from a root prompt.  The solution is to issue (as user) the following:```
xhost +local:
```
Maybe if you issue the same command as root you would get round it (but that still doesn't explain why it's happening)?

---

### Post by dvejnovic on 2005-12-19
OK.
I was reinstall again vmware with sudo user. When I try tu rum it as normal user, get following error:
"Unable to change virtual machine power state: Failed to connect to peer process."

What's wrong??? :confused:

---

### Post by Sanix on 2005-12-20
[QUOTE=MartinG]I sometimes get it the other way round, where I can't start an X app from a root prompt.  The solution is to issue (as user) the following:```
xhost +local:
```
Maybe if you issue the same command as root you would get round it (but that still doesn't explain why it's happening)?[/QUOTE]


I don't have a VMWARE Problem, but had the same error message. Your solution works, but what does it?

---

