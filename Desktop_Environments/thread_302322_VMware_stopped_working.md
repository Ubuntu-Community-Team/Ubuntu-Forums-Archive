---
title: "VMware stopped working"
date: 2006-11-18
forum: Desktop Environments
---

### Post by baylorbear on 2006-11-18
VMware won't load anymore.... I ran some updates this morning, but can't think of any reason for it to just STOP loading... any suggestions?

---

### Post by pdub on 2006-11-18
Make sure your headers match your kernel.

```
uname -a 
```

to show your kernel version

then check where your headers are pointing

```
ls -la /usr/src/linux
```

Should be pointing to the same version of headers as the kernel. If not, then use apt-get to install the proper headers.

Then you need to change the symbolic link i.e.:

```
rm -r /usr/src/linux

ln -s /usr/src/new_headers /usr/src/linux
```


Then run 

```
vmware-config.pl
```

---

