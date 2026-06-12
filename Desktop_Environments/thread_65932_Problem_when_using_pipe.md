---
title: "Problem when using pipe"
date: 2005-09-15
forum: Desktop Environments
---

### Post by jAr0d on 2005-09-15
Hi all !

I have a little problem when I use pipe command lines :
```
yann@ubuntu:~$ find / | grep test
bash: grep: command not found
yann@ubuntu:~$
/code]

It seems to be wrong with all command (like more, cat etc...)

The only way to make it working, is to remove the space between | and grep, like this :

[code]yann@ubuntu:~$ find / |grep test
/home/yann/src/c/overflow_test
/home/yann/src/c/overflow_test/vuln1.c
/home/yann/src/c/overflow_test/vuln1
/home/yann/src/c/overflow_test/exploit_vuln1.c
etc... 
``` 

It's a problem for me, because I always put a space and I need to retry the command by removing the space... I also have a lot of bash scripts that use the command line with space
and I don't want to modify them...

Sorry for my strange english, but i'm french ^^

Thanks :)

Yann.

---

### Post by mlomker on 2005-09-15
I haven't heard of this problem before.

Does **echo $PATH** produce a path that looks normal?

---

### Post by jAr0d on 2005-09-15
Oh yes I think :

```
yann@ubuntu:~$ echo $PATH
/home/yann/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
yann@ubuntu:~$

```

Is it correct ?

Yann.

---

### Post by jAr0d on 2005-09-15
So, I've just done some test and I show you results :
```

yann@ubuntu:~$ lsmod | grep ipv6
bash:  grep: command not found
yann@ubuntu:~$ grepe
bash: grepe: command not found
yann@ubuntu:~$
```

I think the space between | and grep are interpreted as a part of the grep executable name.

What do you think ?

Yann.

---

### Post by mlomker on 2005-09-16
> 
Is it correct ?


You have some user directories before system folders.  Have you made changes to your /home/yann/.bashrc file?  

Grep is in /bin and you have quite a few folders in your path before /bin.  You could try **whereis grep** to verify that you do not have more than one copy.

Then try re-running your command after using my path:

```

export PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/bin/X11:/usr/local/sbin:/usr/local/bin

```

---

