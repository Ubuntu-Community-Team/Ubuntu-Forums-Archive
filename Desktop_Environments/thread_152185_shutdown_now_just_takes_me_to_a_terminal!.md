---
title: "shutdown now just takes me to a terminal!"
date: 2006-03-29
forum: Desktop Environments
---

### Post by Killgore on 2006-03-29
I did a server install on my PC and managed to get X and Blackbox working with some of my favourite apps. The only problem is that when I run the command

```
 sudo shutdown now 
```

It goes through all the Sending processes the TERM signals, but never actually goes down. Im just left staring at root@toolboxlinux. It used to work when I had the default install so im wondering if I may be missing a package.

---

### Post by ispmarin on 2006-03-29
don't know if it helps, but sometimes the apm gave some problems when shutdown a machine... not sure.

---

### Post by taurus on 2006-03-29
How about
```

sudo shutdown -h now

```

---

### Post by Killgore on 2006-04-01
Heheh just after i wrote this post i read the man pages for shutdown. Hmm i wonder what H does? Thats what you get for not reading the help first.

---

### Post by bonzodog on 2006-04-01
yeah, shutdown -h means shutdown and halt. You can also do Shutdown -r which tells it to reboot.

---

### Post by stevea1210 on 2006-04-01
I just use 
```
sudo halt
```
less typing.

from Simpsons episode King size Homer:
> Homer: "Vent radioactive gas?"  [types] Y E S.
       "Sound alertness horn?"  Y E S. [it sounds in the distance]
       "Decalcify calcium ducts?"  Well, give me a Y, give me a...Hey!  All I have to type is Y. 
[to Marge] Hey, Miss Doesn't-find-me-attractive-sexually-anymore: I just tripled my productivity!

---

### Post by ispmarin on 2006-04-03
:d

---

