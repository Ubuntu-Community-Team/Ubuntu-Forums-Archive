---
title: "urgent please help!  sudo issues"
date: 2006-02-18
forum: Desktop Environments
---

### Post by dylanknightrogers on 2006-02-18
I was trying to network my two ubuntu pcs together with nfs and edited the hosts file.  but apparently i didnt do it right because im an idiot and will never be able to network these linux boxes together!!!! :evil: 

this is my entire hosts file

127.0.0.1 localhost.localdomain localhost

i need to add the word a720n after localhost somehow, but cant because i cannot sudo...i get this mesage

dylan@a720n:~$ sudo
sudo: unable to lookup a720n via gethostbyname()

how do i edit /etc/hosts !?!?  please help!!!!

---

### Post by Treebeard on 2006-02-18
Is this the user that was created during install?
(see [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo"))

If you have sudo rights, try
```

$ sudo vim /etc/hosts

press 'i' to start editing
to save the changes en leave vim enter ':qw'

``` to edit the file.

You can "become root" by 
```

$ sudo -s

```

---

### Post by Ruddigger on 2006-02-18
If everything else fails remember to reboot in safe mode or with the live cd.
You can have root access then, make any changes to any files and then reboot normally

---

