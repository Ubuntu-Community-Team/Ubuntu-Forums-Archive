---
title: "how do i manage system services?"
date: 2005-02-06
forum: Desktop Environments
---

### Post by KenLin on 2005-02-06
I always disable unneeded services (isdn, pcmcia, etc) after instll, but I don't see any tool to do that in Ubuntu, GUI or command prompt. Any help?

---

### Post by KenLin on 2005-02-06
bump

---

### Post by evangelion on 2005-02-06
You should be able to use this command
```

sudo /usr/sbin/update-rc.d -f [service] remove

```

[service] can be found in /etc/init.d  if you aren't sure exactly what the service called,  just check out that directory.

There is a curses interface called "sysv-rc-conf" which you might be able to apt-get (not sure if there is an ubuntu package for it,  it may already be on your system).  With that you just uncheck all boot levels of the service you want to stop from running.

Little note; I'm using stock Debian at the moment but I don't see any reason why things would be different for Ubuntu.

---

### Post by KenLin on 2005-02-06
Thanks!

---

### Post by piedamaro on 2005-02-06
Try rcconf :)

---

### Post by evangelion on 2005-02-07
[QUOTE=piedamaro]Try rcconf :)[/QUOTE]
Hey, that one is pretty slick! I had never heard of it before, it's much easier than update-rc.d or sysv-rc-conf (and easier to remember, too!)  :)

---

