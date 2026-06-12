---
title: "How to remove GRUB version number"
date: 2009-05-18
forum: General Help
---

### Post by Minsky on 2009-05-18
Forgive me if this has been covered before, I've recently restored Intrepid from a backup image, after trying out Jaunty but could not put up with the ATI driver problems. However, my grub screen now displays a version number, along with the amount of memory allocated at the top of the display, whereas previously it did not. Does anyone know how to remove this text from the top of the grub screen?

---

### Post by Minsky on 2009-05-26
> **Minsky said:**
> Forgive me if this has been covered before, I've recently restored Intrepid from a backup image, after trying out Jaunty but could not put up with the ATI driver problems. However, my grub screen now displays a version number, along with the amount of memory allocated at the top of the display, whereas previously it did not. Does anyone know how to remove this text from the top of the grub screen?

I would really like to get rid of the text at the top of my GRUB screen. Can anyone help?

---

### Post by lindsay7 on 2009-05-26
You could try to edit the grub menu and take out the lines you do now want. Type "sudo gedit /boot/grub/menu.lst" in the terminal with out the quotation marks. That is a letter l not the number 1 in lst. Take out the lines you do not want and save the file.

---

### Post by Minsky on 2009-05-26
I've had a look in menu.lst but I can't find any reference to the GRUB version number or the memory allocation info. Unless I'm missing something obvious, all I can then think of is that GRUB must be running a service/script prior to menu.lst which displays the version number, and the output of menu.lst is then printed underneath. Any idea if this could be the case?

---

### Post by Minsky on 2009-05-31
I think that the problem lies with Stage 2 of the GRUB process which could be printing the version number. I need to have a look inside it so that I can try to alter it. Does anyone know how if there is a configuration file hidden somewhere in the system so that I could edit Stage 2

---

