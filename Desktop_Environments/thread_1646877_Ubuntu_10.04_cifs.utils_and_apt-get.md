---
title: "Ubuntu 10.04 cifs.utils and apt-get"
date: 2010-12-16
forum: Desktop Environments
---

### Post by metallica1973 on 2010-12-16
when I perform an apt-get update and then attempt to install the package

cifs.utils 

it says that it cannot find the package but in Ubuntu 10.04 it does find it in 10.10. Does this package have another name or is it that the standard repositories to not have it in there list?

---

### Post by cipherboy_loc on 2010-12-16
This is what works for me:
```
sudo apt-get install cifs-utils
```




Cipherboy

---

### Post by metallica1973 on 2010-12-16
According to the Ubuntu package search the package cifs-utils is only present in 10.10 and 11.04.

You must be using 10.10. 

cat /etc/issue

thanks

---

### Post by cipherboy_loc on 2010-12-18
Sorry about that. Yes, I am using Ubuntu 10.10... I just searched for cifs in the lucid repositories, but found it missing. If you really want cifs-utils, you will have to update to 10.10. 




Cipherboy

---

### Post by gmargo on 2010-12-19
In 10.04 Lucid the cifs tools are in the package **smbfs**.

[http://packages.ubuntu.com/lucid/smbfs](http://packages.ubuntu.com/lucid/smbfs)

---

