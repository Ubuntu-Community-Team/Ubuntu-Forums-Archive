---
title: "How to change ubuntu as the first boot item?"
date: 2009-02-05
forum: General Help
---

### Post by fprg on 2009-02-05
I find the ubuntu will be the last boot item when I use  Wubi to install ubuntu in windows. I try to modify the boot.ini file . I want to  move the ubuntu to the first position. 

> [boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\wubildr.mbr
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\wubildr.mbr="Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


unfortunately, I got an Error.

> Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please re-install a copy of the above file.


Who know how to do ?

---

### Post by brandon88tube on 2009-02-05
I see two possible problems.

1.```

default=multi(0)disk(0)rdisk(0)partition(1)\wubild r.mbr
```
There is a space between wubild and the r.mbr

2. I would try using this code instead, but I am not entirely sure. Note: c:\ being the drive you have ubuntu installed on
```

default=c:\wubildr.mbr="Ubuntu"
```

---

### Post by fprg on 2009-02-05
In my used file boot.ini, there is no space between "wubild" and "r.mbr". The space maybe come from the text-edit program I used.

I think, the Microsoft Windows has made the problem intentionally.

---

### Post by lightsout565 on 2009-02-06
I dont believe you can change the order but you can set which one boots first. :KS Boot Windows and right click on my "My Computer" go to properties, go to Advanced, go to "Startup and recovery" and choose the OS from the drop-down field:KS

---

### Post by fprg on 2009-02-09
OK! Now I know how to do.Thanks.

---

### Post by brainac0cult on 2009-02-10
download startup manager from add/remove and see what it can do.

---

