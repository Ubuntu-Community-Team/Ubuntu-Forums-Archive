---
title: "Graphic Booting Options"
date: 2010-07-03
forum: Desktop Environments
---

### Post by andy_t on 2010-07-03
Probably a quick one, I want to see grub then text then login screen rather than any splash screens between grub and login (doesn't display properly since I'm using ATI drivers)... is there a way to see the loading text, ideally like ubuntu live in a higher res with colour?

Cheers!!!

---

### Post by cavalier911 on 2010-07-03
```
sudo nano /etc/default/grub
```
Change this:       
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
To this:           
**GRUB_CMDLINE_LINUX_DEFAULT="quiet"**
For Verbose:       
**#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
Save changes
```
sudo update-grub
```

---

### Post by andy_t on 2010-07-03
That's great, knew it would be simple... any way to bump up the res from 640 to 1024 or 1280?

---

### Post by cavalier911 on 2010-07-04
**My gift to you:**
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by andy_t on 2010-07-04
That's a good reference website, it covers the resolution settings for GRUB but not how to get Ubuntu to display the text loading in a higher resolution - much like the Live CD does.

---

