---
title: "Help with removing module during boot"
date: 2006-02-18
forum: Desktop Environments
---

### Post by ILikeLinux on 2006-02-18
Hi, 

I have this external usb hard disk, which mounts OK and I can 
read and write OK. But after a couple of minutes, the icon 
disappears and the program that was using those files stop
etc. I found out that if I remove a module, then it does not
happen any more.


```
$ sudo modprobe -r  ehci_hcd
```


Hence, I was wondering, if I could automatically remove that
module at boot, or when I plugged in the usb disk. If anybody
knows a solution, please help.

---

