---
title: "GRUB timer termination"
date: 2005-12-20
forum: General Help
---

### Post by Prudentissimus on 2005-12-20
How do you turn off the GRUB timer!!?


and 


How do you make timer for Windows Xp instead of Ubuntu???

---

### Post by aysiu on 2005-12-20
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` Change ```
default 0
``` to something else (probably *default 4*), and change ```
timeout 10
``` to something else (*timeout 5* for five seconds).

I say "probably" 4, because numbering starts at zero, and your Grub menu probably looks like this:

#0 - Ubuntu
#1 - Ubuntu recovery
#2 - Ubuntu memtest
#3 - other operating systems
#4 - Windows

---

### Post by Prudentissimus on 2005-12-20
thank you very much

---

