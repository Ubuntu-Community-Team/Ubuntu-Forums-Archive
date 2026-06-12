---
title: "Edit boot options (got XP and linux)"
date: 2006-08-12
forum: Desktop Environments
---

### Post by stefangranholm on 2006-08-12
I want to change the bootup selection, so XP is defoult if nothing else is selected.

I dont know much, but tried downloading Lilo, didnt work.

So, is there a grafik way of editing the boot ?

---

### Post by AtrejuT on 2006-08-12
well I don't know about a graphical way but it is fairly easy to do in the console. By default you should be using grub, so if you open a console window and enter

sudo nano /boot/grub/menu.lst

you should find a line 
default    0
which you can change to 
default    x
where x is the number of the line your winxp appears in in the boot screen. (start counting at 0)

good luck

---

### Post by Tomosaur on 2006-08-12
Check the link in my sig for a graphical Grub editor.

---

### Post by stefangranholm on 2006-08-13
the grub is good.. thankz a lot

---

