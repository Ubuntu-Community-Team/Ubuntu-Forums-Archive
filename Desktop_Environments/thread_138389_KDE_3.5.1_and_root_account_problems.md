---
title: "KDE 3.5.1 and root account problems"
date: 2006-03-01
forum: Desktop Environments
---

### Post by carrouf on 2006-03-01
Hi all,

Found weird behaviours for root account with Kde 3.5.1 :

- first of all, modifications made with Kcontrol don't work, unless you launch kcontrol with 'sudo kcontrol'. This is a nonsense, I am root already !

- second, where is the '/root/.kde' folder ?! It seems root makes use of a '/root/share' folder instead. I don't know why. How do I get Kde to work with '/root/.kde' folder back again ?



Thanks/

---

### Post by hankeral on 2006-03-02
Perhaps this link will help. It explains how sudo relates to root in ubuntu and how to use graphical programs requiring root permissions. 
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

hank

---

### Post by aysiu on 2006-03-03
Kubuntu's not designed to run a root account. It's designed for sudo.

---

