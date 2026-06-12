---
title: "Network interface card type"
date: 2009-04-23
forum: General Help
---

### Post by yildiz.a on 2009-04-23
How can I learn NIC type on Ubuntu 8.10? Thanks...

---

### Post by dabl on 2009-04-23
In Linux, there are always more than one way.

1. In a console window:

```
sudo dmidecode
```

2. First install hwinfo

```
sudo apt-get update && sudo apt-get install hwinfo
```

then in the console

```
sudo hwinfo
```

3.  (my favorite) Go to getdeb.net here:

[http://www.getdeb.net/browse.php](http://www.getdeb.net/browse.php)

Choose the category "System Tools" and then download the package hardinfo_blahxxx.deb -- make sure to choose the architecture (32-bit or 64-bit) that is for your system.  Install it in the console with 

```
sudo dpkg -i hardinfo_blahblahblah
```

Then run it from your menu -- in Kubuntu it goes to KMenu>Settings -- I'm not sure where it ends up in Ubuntu.

---

### Post by yildiz.a on 2009-04-23
Thanks. I wrote that command and got that which I added as attachment.

---

### Post by dabl on 2009-04-23
Huh -- well that didn't work very well, did it?

OK, open your console and enter ```
lspci
``` and maybe it will show it.

---

### Post by yildiz.a on 2009-04-23
Actually I need NIC model type for QEMU -->

qemu -net nic[,vlan=n][,macaddr=addr][,model=type]

I saw a command in which writes for model like "rtl3819". How did this guy find this number?

---

### Post by dabl on 2009-04-23
Probably lspci will show the model number of the NIC.

---

