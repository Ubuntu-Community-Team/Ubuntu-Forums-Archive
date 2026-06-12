---
title: "synaptic seg fault"
date: 2005-10-15
forum: Desktop Environments
---

### Post by iimess on 2005-10-15
Segmentation fault. Nothing more...

The last time I opened Synaptic was changing all hoary to breezy in repository and did reload/mark all several times.
(Eventually I cancelled the interface and upgraded with apt-get distro-upgrade. Synaptic exited normally)

apt-get update/install/etc works fine
tried remove/install but no luck...

---

### Post by ppl on 2005-10-16
[QUOTE=iimess]Segmentation fault. Nothing more...

The last time I opened Synaptic was changing all hoary to breezy in repository and did reload/mark all several times.
(Eventually I cancelled the interface and upgraded with apt-get distro-upgrade. Synaptic exited normally)

apt-get update/install/etc works fine
tried remove/install but no luck...[/QUOTE]

I get exactly the same problems, and I the process I upgrade are similary to you. Some one have solution or point to some directions could help?

---

### Post by fabpicca on 2005-10-24
i've got the same problem i can post also the result of 
sudo apt-get remove synaptic
and sudo apt-get install synaptic

```
Segmentation faultsts... 0%
```

---

### Post by fabpicca on 2005-10-24
problem solved:

Accordingly to [http://lists.debian.org/deity/2002/03/msg00122.html](http://lists.debian.org/deity/2002/03/msg00122.html)
i've deleted the cache data of apt tool.

Now everything seemes to work fine again.

---

### Post by beckejc on 2008-05-05
Sadly, this problem appears to be reborn in hardy (Xubuntu in my case).

[425653.946808] apt-check[29749]: segfault at de2a1da0 eip b7bf0da1 esp bfc0e110 error 4
[425694.016003] synaptic[29678]: segfault at dd167d98 eip b7e68da1 esp bfca3df0 error 4
[425831.870719] synaptic[30579]: segfault at ddf2ad98 eip b7e7bda1 esp bfc4c5c0 error 4
[425846.172899] synaptic[30582]: segfault at ddf75d98 eip b7ec6da1 esp bfb0fb40 error 4
[425870.732915] update-manager[30586]: segfault at dd294d98 eip b6c79da1 esp bf8e9050 error 4
[425870.942918] update-manager[30584]: segfault at dd323d98 eip b6d08da1 esp bf9e7e40 error 4
[426152.290014] apt-get[30634]: segfault at df0c5d98 eip b7f19da1 esp bfacca30 error 4
[426174.529456] xfce4-panel[5386]: segfault at bbdeee37 eip b7f40fc0 esp bfe59630 error 4
[426246.448677] synaptic[30785]: segfault at ddf40d98 eip b7e91da1 esp bfd4dba0 error 4
[426284.162606] apt-check[30806]: segfault at df0a0d98 eip b7ca0da1 esp bfd72a70 error 4

The problem was fixed by :

sudo rm /var/cache/apt/*.bin

which clears the apt cache.

---

