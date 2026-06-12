---
title: "Need to mount drive via live cd"
date: 2009-01-24
forum: General Help
---

### Post by DougieFresh4U on 2009-01-24
Could some one please provide the codes to mount my hard drive from live cd? I need to fix a problem with wireless and also get updates and wireless will not connect from drive. It connects using live cd.
Thanks

---

### Post by dcstar on 2009-01-24
> **DougieFresh4U said:**
> Could some one please provide the codes to mount my hard drive from live cd? I need to fix a problem with wireless and also get updates and wireless will not connect from drive. It connects using live cd.
Thanks

Install the **pysdm** package and use that, otherwise detailed instructions are just a search away.

---

### Post by DougieFresh4U on 2009-01-24
> **dcstar said:**
> Install the **pysdm** package and use that, otherwise detailed instructions are just a search away.

Don't know about that. I just want simple command to mount drive from live cd, please!

---

### Post by taurus on 2009-01-24
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
df -h
```
Assuming /dev/sda1 is your root filesystem.

---

