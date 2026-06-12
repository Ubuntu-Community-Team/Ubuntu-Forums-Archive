---
title: "How do I autorun the date command before GDM?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by tionik06 on 2006-09-04
My imac has a broken hwclock in it and i need to run the date command before gdm starts to avoid the nautilus and bonobo error. I just wanna run a simple date command to bring it somewhere in 2006 and the computer's date doesnt need to be accurate. Can anyone help?

---

### Post by mssever on 2006-09-04
Edit /etc/init.d/gdm and search for the line ```
log_begin_msg "Starting GNOME Display Manager..."
```
Insert just before that line
```
log_begin_msg "Setting clock..."
date --set="090400002006" #Format: MMddhhmmYYYY
log_end_msg $?
```

---

### Post by tionik06 on 2006-09-04
it made it boot to console.

---

### Post by mssever on 2006-09-04
Are you sure you typed/copied everything right?

What errors are there in /var/log/dmesg and /var/log/daemon? You can get a graphical environment by typing startx.

---

