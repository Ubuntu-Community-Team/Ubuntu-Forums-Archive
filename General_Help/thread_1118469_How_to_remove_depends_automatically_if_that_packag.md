---
title: "How to remove depends automatically if that package is not installed from source?"
date: 2009-04-07
forum: General Help
---

### Post by Kelen.Chang on 2009-04-07
Some packages downloads from web(or compile and make install by yourself if you got the sources codes). they are maybe require some depends that you haven't installed. How to get it? in my case is install those depends with command "sudo aptitude install <packages depends name>". 
But my question is How to remove the depends automatically when i uninstall the main package. just like purge a packages that you install from source, and the depends will be purged automatically with the main package together.

---

### Post by kpkeerthi on 2009-04-07
[deborphan]("http://www.debian-administration.org/articles/134") might help.

---

### Post by fprg on 2009-04-07
try the command:
> sudo apt-get autoremove

I also think it cannot do everything unless the log file is correct. If the log file is failed,the used packages may be removed.

---

### Post by Kelen.Chang on 2009-04-08
> **kpkeerthi said:**
> [deborphan]("http://www.debian-administration.org/articles/134") might help.

Dude, you really do me a big favor.  i really appreciate that. :popcorn:

---

