---
title: "gedit /etc/bluetooth/hcid.conf"
date: 2005-10-14
forum: Desktop Environments
---

### Post by z!cHz@cH on 2005-10-14
Could someone post the original Hoary Hedgedog version of this file for me?

I installed 5.10 today.
Now i have some Bluetooth issues that i didnt have using 5.04. 
The problem should be in this file.

thanks in advance.

---

### Post by ranf on 2005-10-14
[QUOTE=z!cHz@cH]Could someone post the original Hoary Hedgedog version of this file for me?

I installed 5.10 today.
Now i have some Bluetooth issues that i didnt have using 5.04. 
The problem should be in this file.[/QUOTE]
There doesn't seem to be an updated version with the upgrade to Breezy:
```

ranf@schlepp:~ $ la /etc/bluetooth/
insgesamt 28
drwxr-xr-x    2 root root 4096 2005-10-14 17:43 ./
drwxr-xr-x  132 root root 8192 2005-10-14 19:50 ../
-rw-r--r--    1 root root 1399 2005-10-03 11:12 hcid.conf
----------    1 root root   72 2005-08-24 20:51 link_key
-rw-r--r--    1 root root    5 2005-08-23 23:13 pin
-rw-r--r--    1 root root  317 2004-08-13 05:58 rfcomm.conf

```

If there were  newer version it would be named `hcid.conf.dpkg*' or so.

---

