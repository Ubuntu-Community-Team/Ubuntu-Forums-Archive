---
title: "terminal text editor"
date: 2005-01-28
forum: Desktop Environments
---

### Post by gogodidi on 2005-01-28
is there one?
I need to change the fstab file, and i can't get to it.

even if I chmod 0777 it, I still can't save to it...

---

### Post by Rancoras on 2005-01-28
```
sudo nano /etc/fstab
``` 

Should get you what you want.
If you want to do it in a gui editor:

```
sudo gedit /etc/fstab
```

When prompted for the password, enter the password of the account that you created during install.

---

### Post by Perfect Storm on 2005-01-28
Though everyone have there favorite text editor program.

I usually use gedit when in desktop envoriment (how the heck do you spell that word  :confused: )
and nano when I not working in the desktop envoriment (I need some spelling hours)

If you are using KDE there's kedit.

---

### Post by Rancoras on 2005-01-28
[QUOTE=Artificial Intelligence]envoriment (how the heck do you spell that word  :confused: )[/QUOTE]

environment

---

### Post by Perfect Storm on 2005-01-28
aaah thanks **writing it down**  :mrgreen:

---

### Post by jerrynew2linux on 2005-01-30
For newbies like myself, Midnight Commander is a good place to begin.  Log in as root, type "mc" and you are good to go.

---

### Post by fng on 2005-01-30
Other console editors : pico, vim, ...
Other gui editors : bluefish, screem, ...

---

### Post by thekore on 2005-01-30
pico, nano, vi, vim, joe are a few... not sure tho if i had to install joe personally or if it was already installed... i cant remember :s

---

