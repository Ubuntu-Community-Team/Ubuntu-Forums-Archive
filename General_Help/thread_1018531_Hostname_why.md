---
title: "Hostname why?"
date: 2008-12-22
forum: General Help
---

### Post by zoomiest on 2008-12-22
I am building LAMP server following [THIS tutorial]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06"), where it mentions that the results of the commnad

```
hostname
```
...and 
```
hostname -f
```
...needed to return the same result.

Mine weren't, so I had to manually edit /etc/hosts and the /etc/hostname to match. 

1) is that okay (is that the right way to do it?)
2) why do they have to match? what are the implications if they don't?

---

### Post by fragos on 2008-12-22
/etc/hostname is your system name as used in internaly. /etc/hosts is for networking. For example if your hostname is also /etc/host you can use it on your LAN as in "hostname.local" instead of an IP. Very handy if you use DCHP on your LAN.

---

