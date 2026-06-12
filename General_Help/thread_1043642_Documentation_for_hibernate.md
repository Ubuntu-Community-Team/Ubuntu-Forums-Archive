---
title: "Documentation for hibernate"
date: 2009-01-18
forum: General Help
---

### Post by Burmuda on 2009-01-18
Hi,
where can I find the documentation of the hibernate feature of Ubuntu? Recently I changed my swap partition (edited fstab) and now everytime I try to hibernate i get " PM: Cannot find swap device, try swapon -a.". 
However swapon -s states:
```
 Filename				Type		Size	Used	Priority
/dev/sdb9                               partition	20643484	298036	-1

```

So I guess I need to change the device in some kind of hibernate configuration file?

Edit: I'm using Ubuntu 8.10

---

### Post by ajgreeny on 2009-01-18
Is your swap actually enabled?  What does```
 free -m
``` show?

---

### Post by Burmuda on 2009-01-18
```

             total       used       free     shared    buffers     cached
Mem:          2007        791       1216          0         12        168
-/+ buffers/cache:        610       1397
Swap:        20159        225      19934

```

---

### Post by ajgreeny on 2009-01-18
Yes it is enabled so I don't know where to go from here.

---

### Post by Burmuda on 2009-01-19
Yes, that's why I'm searching for some kind of documentation for hibernate... :confused:

---

### Post by Burmuda on 2009-01-20
I was able to fix it by using uswsusp.
# apt-get install uswsusp
change/add SLEEP_MODULE="uswsusp" in /etc/pm/config.d/00sleep_module 
edit /etc/uswsusp.conf 
  change resume device to actual swap partition
  change image size to RAM size (in byte)

Nevertheless a documentation of hibernate would be very nice...

---

### Post by maynardp on 2009-03-09
There is some documentation but I'm wishing there was a howto.  (Hibernate is working on my system, but suspend is a total mess.)

```
man -k hibernate
```

```

pm-action (8)        - Suspend or Hibernate your computer
pm-hibernate (8)     - Suspend or Hibernate your computer
pm-is-supported (1)  - Test whether suspend or hibernate is supported.
pm-suspend (8)       - Suspend or Hibernate your computer
pm-suspend-hybrid (8) - Suspend or Hibernate your computer

```

pm-hibernate is the best place to start.

---

