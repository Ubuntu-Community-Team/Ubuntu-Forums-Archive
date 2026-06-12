---
title: "Grub Error 22"
date: 2009-01-30
forum: General Help
---

### Post by cmiller8604 on 2009-01-30
I was using a disk partionor to copletly delete my linux partion and now every time i boot up  grub tries to load and gives me a error 22, theres is no linux anymore though and now the only way i can get to windows is through my recovery disk.

---

### Post by logos34 on 2009-01-30
Grub stage1/1.5 is looking for the menu.lst (i.e. the grub menu screen)--stored in /boot/grub---but since you deleted / it can't find it.  Hence the error.

Restore windows bootloader to the MBR either through the recovery disk (if it allows you to go into 'Recovery console', at the prompt do 'fixmbr'), or else use Super Grub disk (see link in my signature)

---

### Post by cmiller8604 on 2009-01-30
Thanks alot   worked perfectly

---

