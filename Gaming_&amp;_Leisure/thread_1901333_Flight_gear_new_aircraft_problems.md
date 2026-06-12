---
title: "Flight gear new aircraft problems"
date: 2011-12-28
forum: Gaming &amp; Leisure
---

### Post by edmundac on 2011-12-28
Hello, I am having trouble adding new aircraft to Flight gear on Ubuntu 11.10. When I try dragging an aircraft folder into usr/share/games/Flight gear/Aircraft I am told I do not have permission to move the file. I do not know what to do as I am a new user of Ubuntu. Any tips would be greatly appreciated. Thanks

---

### Post by Perfect Storm on 2011-12-28
Instead check for hidden files in your home directory for something similar to .flightgear and put it there. 

You only mess with the system files if it's absolutely necessarily.

---

### Post by MrSpike16 on 2011-12-28
To put the folders in usr/share/games/Flight gear/Aircraft you will need to open the Terminal application and run this command:
```
gksudo nautilus
```

Just be careful and once done close Nautilus.  You are messing in your system files and can do damage if not careful.  

The aircraft folders need to go into that location.

---

