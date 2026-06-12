---
title: "[SSH] usermod --&gt; no more sudo  :-("
date: 2005-10-12
forum: Desktop Environments
---

### Post by szdavid on 2005-10-12
Hello,

I am using ssh and I made a
```
sudo usermod -G szdavid cvs
```

The thing is that szdavid is my sudo user ; now, when i am doing sudo command :
```
sudo ls /etc
szdavid is not in the sudoers file.  This incident will be reported.

```

Help  :-(

Thx

---

### Post by adwait on 2005-10-12
I am not really sure what usermod means, but you can add yourself to sudoers list again. To do this, login as root and then use
```
visudo
```

Add the line
```
szdavid          ALL= (ALL)ALL 
```

---

### Post by ben ogle on 2005-10-19
Apparently usermod takes you out of all groups except the group specified. 

So you need to use adduser and add yourself to the admin group.

I did the same thing about 30 minutes ago but I dont have my root user enabled. Crap. I dont know what to do. Recovery mode? Can I just reboot, choose it and it'll give me privileges to add myself back to the admin group?

I dont want to reinstall.

Ben

---

