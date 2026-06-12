---
title: "grub menu.list didn't update"
date: 2009-04-30
forum: General Help
---

### Post by cacaegg on 2009-04-30
hi, i have some problem with my /boot/grub/menu.lst
the problem is that even i update the new version linux kernel,
the menu.lst still remain the same, so even i reboot still 
i am using the old kernel. 

is there some way to rebuild my menu.lst ?

---

### Post by 3Miro on 2009-04-30
Try System -> Admin -> Startup Manager. If that doesn't work, try installing a more advanced grub editor (I have used KGrubEditor, but it is a KDE app, it will work under Gnome, but it will install many other things that you probably don't need).

Alternatively you can edit the thing yourself:
```

sudo cp /boot/grub/menu.list /boot/grub/menu.list_mybackup
sudo gedit /boot/grub/menu.list

```

---

### Post by cacaegg on 2009-04-30
tks!!  i edit the file directly and it works!!  :)

---

