---
title: "devices aren't recognised"
date: 2008-01-26
forum: Desktop Environments
---

### Post by pfabrikant on 2008-01-26
hey,
i just updated my xubuntu to the 7.10 version. unfortunately, my computer stopped recognizing the external devices (cd-rom, usb sticks). when i load a cd or insert a usb disc,  both the device manager and the file manager don't recognise it. strangely enough, i can burn data (which means the burniing application recognizes the empty cd i insert, no ?).
 I looked through the trouble shooting guides but found nothing that answered my question... 
any suggestion ?
thanks a lot in advance
 a complete newbie

---

### Post by MasterJS on 2008-01-26
The problem might be with the Thunar Volume manager. Check this by either installing it or if it's installed, it might have to get updated. So, go to the terminal and type
 ```
sudo apt-get install thunar-volman
```

---

