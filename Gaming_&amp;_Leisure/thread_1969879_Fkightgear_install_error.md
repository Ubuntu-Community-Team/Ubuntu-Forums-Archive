---
title: "Fkightgear install error"
date: 2012-04-30
forum: Gaming &amp; Leisure
---

### Post by jmore9 on 2012-04-30
I am using 12.04 Ubuntu and tried to install Flightgear using synaptic and got the following error/s :

E: fgfs-base: subprocess installed post-installation script returned error exit status 1
E: fgfs-atlas: dependency problems - leaving unconfigured
E: flightgear: dependency problems - leaving unconfigured

Anyone got any ideas i googled long time nothing worked.  there is a couple of posts on launchpad.  Just thought i would check on the forum.

Thanks in advance for any help in advance

---

### Post by ubudog on 2012-05-01
Could you try: 
```
sudo dpkg --configure -a
sudo apt-get install -f

```

---

### Post by Yellow Pasque on 2012-05-02
[https://bugs.launchpad.net/ubuntu/+source/fgfs-base/+bug/942886](https://bugs.launchpad.net/ubuntu/+source/fgfs-base/+bug/942886)

---

### Post by jmore9 on 2012-05-16
Fixed it by just removing un-installing what ever was trying to install

---

