---
title: "VMWare problem"
date: 2006-10-13
forum: Desktop Environments
---

### Post by SexyPastry on 2006-10-13
im installing the vmware server just curious wut does this mean:

```
What is the location of the "make" program on your
machine? 
```


and wut do i type for that thnx

(sorry new to linux)

---

### Post by Trab on 2006-10-13
it means that make (a program) is not installed correctly.
before trying to install vmware, go to a command line and type
```

sudo apt-get install build-essentials make

```
should then work.

---

