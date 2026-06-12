---
title: "Kernel header files"
date: 2006-06-08
forum: Desktop Environments
---

### Post by dvanleur on 2006-06-08
Hello,

At the moment i trying to install vmware on Ubuntu 6.06, but the installation asks for the location of de  kernel header files, where can i find those files, or can i download those files?

Thanks.

---

### Post by jalm111 on 2006-06-10
Install linux-headers-2.6.15-23-your_architecture from synaptic than run the config script again.

---

### Post by jamesrw on 2006-06-14
thnx

---

### Post by az on 2006-06-14
vmware player is in multiverse.

---

### Post by lamego on 2006-06-14
From the command line:
  sudo apt-get install linux-headers-`uname -r`

---

### Post by mfaridi on 2006-06-15
I download kernel header can I install it with this command

dpkg -i kernel*.deb

can I install kernek source with this command

dpkg -i kernek-source*.deb

---

