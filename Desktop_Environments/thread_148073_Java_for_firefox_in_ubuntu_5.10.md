---
title: "Java for firefox in ubuntu 5.10?"
date: 2006-03-21
forum: Desktop Environments
---

### Post by JohnnyWalker on 2006-03-21
How can I get Java for firefox, using ubuntu 5.10?

I was told to do the below, but as you can see, it does not work.

vmware@vmware-bavm:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... 0%

Building dependency tree... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate

---

### Post by Perfect Storm on 2006-03-21
*<Double post>*

---

### Post by Perfect Storm on 2006-03-21
You need to add some stuff to your sourcelist, PLF.


(this only work for breezy i386 structure)
```
sudo gedit /etc/apt/sources.list

```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

save and exit.

```
sudo apt-get update
sudo apt-get install sun-j2re1.5
```


Warning: when adding this to your sourcelist there a some stuff which are illegal in the US (media codecs etc.), so it's on your own risk.

---

### Post by gnu2tux on 2006-03-21
Please see the official Ubuntu word on Restricted Formats/Java:

[https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249")

---

