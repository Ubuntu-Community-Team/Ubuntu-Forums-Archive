---
title: "bios setup or grub doesn't respond to keyboard"
date: 2006-08-27
forum: Desktop Environments
---

### Post by royg1234 on 2006-08-27
Hey.  My keyboard seems to not work when I first start up.  I can't do anything witht the grub menu, and I can't even hit [DEL] to go into the BIOS setup.  Anybody know how to fix this?

Thanks.

---

### Post by Saibot on 2006-08-27
Are you using a USB keyboard?  If you are then try plugging in a PS/2 keyboard if you have one available - or if your keyboard came with a USB to PS/2 adapter use that.  You should be able to get into bios then, and there could be an option to enable the bios to recognize USB keyboards.

---

### Post by royg1234 on 2006-08-27
nope.  It's a PS/2 keyboard (but the mouse is USB (?)).

---

### Post by bullgr on 2006-08-27
maybe it's a stupid answer, but is the keyboard working for sure? can you boot in winblows to try it or to another pc?

---

### Post by royg1234 on 2006-08-27
yes.  the keyboard works for sure.  and I can't boot into Windows because Ubuntu is default in grub and the keyboard doesn't work at this point.  It only starts working afaik when Ubuntu's login screen shows.

Anybody?

---

### Post by royg1234 on 2006-08-30
anybody?  please?

---

### Post by rockz on 2006-09-24
I have a similar problem, but i think that my problem  is more difficult to solve. I cant access the BIOS setup and i cant use grub menu to choose windows. I need to access BIOS setup to enable USB keyboard support, but my ps/2 is broken. I dont know what do to enable USB keyboard support without enter in BIOS setup.

---

### Post by alecjw on 2006-09-24
Well, as a temporary solution: when you want to boot windoze, open /boot/grub/menu.lst. There should be a line saying default x (probably 0). If if wndoze is the 4th option in the GRUB list, change it to default 3, if windoze is the 5th opeion default 4 and so on. Then change it back to the original when you want to boot ubuntu again. But as I said, it's only a temporary solution.

---

