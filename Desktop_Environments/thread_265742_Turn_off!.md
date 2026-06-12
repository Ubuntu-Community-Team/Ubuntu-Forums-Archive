---
title: "Turn off!"
date: 2006-09-26
forum: Desktop Environments
---

### Post by inktomi7 on 2006-09-26
Hi there,

I shut down my Ubuntu and everything seems to be going fine. The whole shutdown procedure seems to be working. I even hear the hard disk turning off. However, the computer remains on and appears to be frozen. 

(The problem started yesterday after installing EMC2 cnc software. I recall that it modified something from GRUB, but I'm not so sure :-k ). Anyone can suggest a fix? :-D 

Thanks

---

### Post by pay on 2006-09-26
Look in your grub file and see if there is anything unusual```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by inktomi7 on 2006-09-26
Nothing strange compared to a typical menu.lst file on the net

---

