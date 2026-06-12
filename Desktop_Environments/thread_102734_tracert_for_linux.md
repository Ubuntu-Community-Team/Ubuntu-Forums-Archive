---
title: "tracert for linux?"
date: 2005-12-12
forum: Desktop Environments
---

### Post by pilotcp on 2005-12-12
hello all, 
i am not sure if this is the right forum, but is there a command in terminal that is the same as tracert for windows?

Charlie

---

### Post by AndersAA on 2005-12-12
apt-cache search tcptrace might get you some hits (I'm not on my ubuntu box right now).

//edit, infact the one from windows is actually bsd's, and you can get bsd's running in linux very easily.

---

### Post by Vytas on 2005-12-12
Using synaptic/apt-get/whatever find and install **traceroute** (in supported packages).
The use is simple and straightforward, try

```
traceroute www.google.com
```

---

### Post by ttp on 2005-12-12
tracepath may be installed by default

---

### Post by pilotcp on 2005-12-12
thanks guys, traceroute worked (it wasn't already installed)!

thanks a lot!

Charlie

---

