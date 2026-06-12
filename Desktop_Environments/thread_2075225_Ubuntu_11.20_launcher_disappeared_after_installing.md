---
title: "Ubuntu 11.20 launcher disappeared after installing Nvidia Driver"
date: 2012-10-23
forum: Desktop Environments
---

### Post by fatihalp on 2012-10-23
Yesterday, I have installed and updated Nvidia driver from Ubuntu Software Center. After restarting my PC launcher disappeared like in screen:
[http://tinypic.com/r/10zo8ro/6](http://tinypic.com/r/10zo8ro/6)

I have restarted, updated and re-installed Unity. But it doesn't work for me. I think there is problem with graphic/nvidia configuration.

---

### Post by fatihalp on 2012-10-23
I have removed Nvidia (current) Driver from Software Center. It solved problem but I feel it's not updated driver which I'm using now?

---

### Post by bogan on 2012-10-23
Hi!, **fatihalp**,

Please Post:```
 uname -ar
sudo apt-cache policy nvidia-current*
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao!, **bogan**.

---

