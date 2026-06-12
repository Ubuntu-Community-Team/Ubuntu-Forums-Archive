---
title: "[SOLVED] Is there a way to hide windows xp on grub menu??"
date: 2008-12-13
forum: General Help
---

### Post by morbid_bean on 2008-12-13
This may sound strange. I dual boot windows xp and ubuntu intrepid and I was wondering if there was a way to hide windows xp on the grub list but still have a way of booting  into xp.

---

### Post by fubbleskag on 2008-12-13
have not tested this, but presumably you could change the title of the windows entry in /boot/grub/menu.lst to only blank spaces

---

### Post by adult swim on 2008-12-13
you can hide the whole menu and have ubuntu boot by default. to do that you need to run ```
gksudo gedit /boot/grub/menu.lst
``` and make the changes 
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```
this way when you start your computer you wont see the option of ubuntu or windows and in five seconds, ubuntu will boot.  if you ever want to run windows, press the ESC key during the 5 second pause at boot and you can select windows from the list.

---

### Post by morbid_bean on 2008-12-14
Both Great Answers....thanks! :guitar:

---

