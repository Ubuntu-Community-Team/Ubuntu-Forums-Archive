---
title: "compile from source question"
date: 2009-05-06
forum: General Help
---

### Post by fouadk on 2009-05-06
hi everyone,

i have compiled from source proftp because im interested in version 1.3.2rc4 which is not present in the repos...

my question is the following, how do i add a program compiled from source to the startup scripts that is i want proftp to start when i reboot the server ???

another question, how do u restart processes when u change their configuration files ?
that is if i installed proftp from the repos i would do the following after changing the configuration file:
```
sudo /etc/init.d/proftpd restart
```

but the compiled version does not have this easy solution, i have tried looking in the top command but i couldnt find the proftp process in order to kill it and start it again, so how do i do it ?

please help..
thanks in advance

---

### Post by danwood76 on 2009-05-06
If you want to kill a process from the command line do:
```

killall PROCESS_NAME

```
also when you compile from source you may have to create or install the init scripts manually.
You could cheat and install the one from the repos and then 'sudo make install' your compiled version over the top of it.

When you compile software when you configure it to make it overwrite the default software you have to change the install prefix.
This is normally done when configuring so the configure script input would look like this:
```

./configure --prefix=/usr

```
Although I have never compiled proftpd this is the usual case for software.

---

### Post by fouadk on 2009-05-06
i discovered the cheat by myself by mistake but you still have to tweak a bit the init script....

anyway...thanks a lot

---

