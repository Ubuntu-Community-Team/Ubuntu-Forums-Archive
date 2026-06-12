---
title: "cannot mount the partation"
date: 2008-12-14
forum: General Help
---

### Post by ananthram on 2008-12-14
my problem: first i had windows and i installed  and used dual booting then now my windows crashed so i formatted that partation and loaded again and now the grub was not loading it was going to windows directly so used the live cd and brought the grub by sudo grub find /boot/grub/stage1 the output was hd0,5 so then i used the cmd root (hd0,5) and setup(hd0) quit .then now when i started to boot i got the menu asking to boot ubuntu or xp then when i choose ubuntu or its recovery it says the partation cannot be mounted.

---

### Post by Bucky Ball on 2008-12-14
At the grub, choose a kernel, hit 'e' for edit and make sure that is booting from the right partition, ie  (hd0,6), or whatever it might be. If not, go to that line and hit 'e' again and correct it. Hit 'return' then 'b' for boot.

It will be (hd?,?) if you Ubuntu install is on another physical disk.

If this does the trick, you need to go:

```
sudo nano /boot/grub/menu.lst
```

then change the details in there to make it permanent. Reboot and make sure.

Incidentally, use 'sudo' rather than 'sudo su' to become root. It is safer.

---

### Post by ananthram on 2008-12-14
thanks boss i had to edit it to hd0,5 and now it works, no i feel the meaning of ubuntu:-"humanity to others".

---

### Post by Bucky Ball on 2008-12-14
A pleasure and welcome to the forums. :)

---

