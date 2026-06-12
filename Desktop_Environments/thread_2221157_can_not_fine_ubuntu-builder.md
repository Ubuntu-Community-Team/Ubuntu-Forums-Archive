---
title: "can not fine ubuntu-builder"
date: 2014-04-30
forum: Desktop Environments
---

### Post by williambiggs31 on 2014-04-30
I added the ppa for ubuntu-builder but when I try to install it . It says Unable to locate package ubuntu-builder where can I find it

---

### Post by deadflowr on 2014-05-01
Did you refresh the package list
```
sudo apt-get update
```
?

---

### Post by williambiggs31 on 2014-05-01
yes and gpt this Failed to fetch [http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/f-muriana/ubuntu-builder/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

---

### Post by deadflowr on 2014-05-01
That ppa only goes to saucy right now.
What you can try is edit the ppa file in /etc/apt/sources.list.d folder.
changing it from trusty to saucy.

[s]Note this would be a temporary change, and when the trusty version comes change it back.[/s]

**Edit**: Nevermind, looky here
[https://launchpad.net/ubuntu-builder/+announcement/12508](https://launchpad.net/ubuntu-builder/+announcement/12508)

seems saucy is the last version you can get.

---

### Post by williambiggs31 on 2014-05-01
thanks

---

