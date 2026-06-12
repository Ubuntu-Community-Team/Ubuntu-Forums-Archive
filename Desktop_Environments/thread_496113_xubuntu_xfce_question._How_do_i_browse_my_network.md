---
title: "xubuntu xfce question. How do i browse my network ?"
date: 2007-07-08
forum: Desktop Environments
---

### Post by Balinsky on 2007-07-08
I really like to access my network shares on my xubuntu box but i have no idea where to navigate to it. its real easy with ubuntu but i am missing something in xfce...

thx 
jebsky

---

### Post by julep on 2007-07-08
I can't give you a howto on this because I've never done it myself but I've see it done in another ubuntu based distribution (also running xfce) named Linux Mint. The package you need is fusesmb, you can get info on the package with ```
sudo apt-cache show fusesmb
```
The package uses the fuse kernel module to mount windows shares in your network neighborhood somewhere on your file system. I don't know if you need to install samba or not and I'm not sure if it mounts shares read only or read-write. 

Sorry I can't give you any more help, hopefully someone else can chime in.

julep

---

### Post by Balinsky on 2007-07-08
i found a useful how to and used fuse and mounted the network

---

### Post by julep on 2007-07-08
Cool!

---

### Post by eidam655 on 2007-11-04
where did you find that useful how-to? :) it would help others :)

---

