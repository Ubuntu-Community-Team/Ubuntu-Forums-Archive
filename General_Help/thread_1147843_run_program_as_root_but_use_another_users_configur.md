---
title: "run program as root but use another users configuration"
date: 2009-05-03
forum: General Help
---

### Post by justjoshingyou on 2009-05-03
Hello I would like to know how to run a program (Mozilla Firefox 3.0.10) as root but still use the user's configuration. Mainly I would start firefox by using 
```
josh@josh-office:~$ firefox
```
which has my themes and my plug-ins, home page(configuration)
---see Screenshot1.png---

Now if I would run it as
```
josh@josh-office:~/Desktop$ gksudo firefox
```
I would get firefox being run using the root's configuation(which is nothing)
---see Screenshot2.png---

I would like to run it as root and use my configuration, which is probably found in  /home/josh/

---

### Post by DGortze380 on 2009-05-03
> **justjoshingyou said:**
> Hello I would like to know how to run a program (Mozilla Firefox 3.0.10) as root but still use the user's configuration. Mainly I would start firefox by using 
```
josh@josh-office:~$ firefox
```
which has my themes and my plug-ins, home page(configuration)
---see Screenshot1.png---

Now if I would run it as
```
josh@josh-office:~/Desktop$ gksudo firefox
```
I would get firefox being run using the root's configuation(which is nothing)
---see Screenshot2.png---

I would like to run it as root and use my configuration, which is probably found in  /home/josh/

start by copying your configuration to root....?

sudo cp ~/.firefox /root/.firefox

---

