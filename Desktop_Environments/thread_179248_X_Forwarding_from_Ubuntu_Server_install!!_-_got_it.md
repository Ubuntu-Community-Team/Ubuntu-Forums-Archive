---
title: "X Forwarding from Ubuntu Server install!! - got it to work"
date: 2006-05-19
forum: Desktop Environments
---

### Post by helmet on 2006-05-19
Here's how I got it to work.

the server install doesn't install anything related to X so nothing works.

```
sudo apt-get install xauth
```

will install the xuath needed for at least X forwarding. then on windows cygwin start-x-server scripts, putty, xforward variable localhost:0 and go

```
gedit&
```

works now! also for any other things like synaptic, etc

---

