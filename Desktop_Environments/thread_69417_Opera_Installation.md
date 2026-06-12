---
title: "Opera Installation"
date: 2005-09-26
forum: Desktop Environments
---

### Post by donkey2 on 2005-09-26
I get an error when I try to install Opera (it's free now):


# sh install.sh

Files will be installed as follows:
-----------------------------------------------------------
 Wrapper Script : /usr/bin
 Binaries       : /usr/lib/opera/8.50-20050916.5
 Plugins        : /usr/lib/opera/plugins
 Shared files   : /usr/share/opera
 Documentation  : /usr/share/doc/opera
-----------------------------------------------------------
Is this correct [ y,n,c | yes,no,cancel ] ?
y

System wide configuration files:
  /etc/opera6rc
  /etc/opera6rc.fixed
**  cannot be installed with the prefix "/usr".**
Do you want to install them [ y,n | yes,no ] ?
y



Then it quits. Any ideas?


[http://www.opera.com/download/]("http://www.opera.com/download/")

---

### Post by cowlip on 2005-09-26
HI, i don't know, but you're not using the deb?

---

### Post by DJ_Max on 2005-09-26
It should be 
```
sudo sh install.sh
```

---

### Post by macgyver2 on 2005-09-26
[QUOTE=cowlip]HI, i don't know, but you're not using the deb?[/QUOTE]
Yes, try this deb:

[ftp://ftp.opera.com/pub/opera/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb](ftp://ftp.opera.com/pub/opera/linux/850/final/en/i386/shared/opera_8.50-20050916.6-shared-qt_en_etch_i386.deb)

---

