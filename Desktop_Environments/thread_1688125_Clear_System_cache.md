---
title: "Clear System cache"
date: 2011-02-15
forum: Desktop Environments
---

### Post by raunhar on 2011-02-15
Ubuntu 10.10
How do I clear the System cache memory.
For the past few days , I am facing problem in opening websites (firefox & Chrome).
I have to restart the laptop and then access the web sites.

---

### Post by Jahid65 on 2011-02-15
You can use Bleachbit. Search for it in software center/synaptic manager

---

### Post by Grenage on 2011-02-15
> **raunhar said:**
> Ubuntu 10.10
How do I clear the System cache memory.
For the past few days , I am facing problem in opening websites (firefox & Chrome).
I have to restart the laptop and then access the web sites.

I restart the service to clear DNS cache:

```
sudo /etc/init.d/nscd restart
```

To clear web cache, I use the firefox option.

---

### Post by raunhar on 2011-02-15
It is not only with internet, but if I replace a CD/DVD with another one, UBUNTU shows the previous one and not the currently inserted into the drive.
This is not when I use the laptop on Windows.

---

