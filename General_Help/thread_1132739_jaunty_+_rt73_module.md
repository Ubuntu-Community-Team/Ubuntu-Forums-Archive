---
title: "jaunty + rt73 module?"
date: 2009-04-22
forum: General Help
---

### Post by Miaxi on 2009-04-22
The jaunty update didn't solve the problems with my DWL-G122 w-lan adapter, so I want to install the serialmonkey module again, like I had it in 8.10. However, I ran into problems with some file structure changes? I understand that /etc/modprobe.d/blacklist is called blacklist.conf now and did the entries to get rid of the old modules, but modprobe -v rt73 doesn't activate the new module for some reason? I followed this guide [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) .

---

### Post by skymera on 2009-04-22
I use the Belkin F5D7050 USB adaptor for my laptop.
It uses the module rt73usb 

TrY:

```
 sudo modprobe rt73usb 
```

---

