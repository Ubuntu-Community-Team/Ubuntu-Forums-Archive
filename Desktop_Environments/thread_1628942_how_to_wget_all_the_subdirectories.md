---
title: "how to wget all the subdirectories"
date: 2010-11-23
forum: Desktop Environments
---

### Post by jamesbon on 2010-11-23
I want to download all the folders available here

[http://www.cs.fsu.edu/~baker/devices/lxr/source/2.6.25/ldd-examples/](http://www.cs.fsu.edu/~baker/devices/lxr/source/2.6.25/ldd-examples/)

but when I do a 
```
wget http://www.cs.fsu.edu/~baker/devices/lxr/source/2.6.25/ldd-examples/
```
I just get the index.html page what should I be doing so that I can have all those subdirectories also ?

---

### Post by viralmeme on 2010-11-23
> **jamesbon said:**
> I want to download all the folders available here .. what should I be doing so that I can have all those subdirectories also ?
wget -r -np [www.cs.fsu.edu/~baker/devices/lxr/source/2.6.25/ldd-examples]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/source/2.6.25/ldd-examples")

---

### Post by iiiears on 2010-11-23
man wget hurts the eyes with the number of --switches -l(number) controls the depth from the requested directory.

Best Wishes,

---

### Post by geoffmcc on 2010-11-23
I think you may find that alot of sites will have protection against wget in the form of a user-agent string

---

