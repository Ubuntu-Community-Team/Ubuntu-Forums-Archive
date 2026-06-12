---
title: "Restarting X"
date: 2006-01-12
forum: General Help
---

### Post by renzokuken on 2006-01-12
ok, quick question,

when i restart X with the old Ctrl+Alt+Backspace, sometimes it returns me to the GDM login screen, and other times to the text based commandline screen, seemingly at random as to which one

if it goes to the commandline/terminal/console (whatever its called) screen, how do i get back to graphical GDM screen without having to do a "sudo reboot"?

---

### Post by socrazy143 on 2006-01-12
```
startx
```

---

### Post by kaamos on 2006-01-12
```
sudo /etc/init.d/gdm restart
```

---

### Post by renzokuken on 2006-01-12
thanks guys

---

