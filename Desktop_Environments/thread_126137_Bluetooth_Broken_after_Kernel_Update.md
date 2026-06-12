---
title: "Bluetooth Broken after Kernel Update"
date: 2006-02-05
forum: Desktop Environments
---

### Post by noahjb on 2006-02-05
Hello. I use an apple wireless mouse with ubuntu and it was working fine until I updated the kernel to 2.6.12-10 a while ago. Then it simply stopped working. 
I reinstalled all the bluez stuff and it still doesn't work.
```
sudo hcitool scan
``` results in ```
Device is not available: No such device
``` and  ```
sudo hidd --connect 00:0A:95:03:24:C2
``` (to the MAC address of the mouse) results in  ```
Can't get device information: No route to host
``` I've been using the trackpad, but it's really annoying, Is there any way to fix this??

---

### Post by noahjb on 2006-02-06
Well, it is working now. Not sure why, I didn't change anything except that I didn't touch the mouse before the login screen appeared. I haven't tested to see if that is actually related, though.

---

