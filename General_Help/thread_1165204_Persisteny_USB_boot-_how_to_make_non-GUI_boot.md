---
title: "Persisteny USB boot- how to make non-GUI boot?"
date: 2009-05-20
forum: General Help
---

### Post by emarkay on 2009-05-20
Without GRUB, I can't seem to find the option to get the scrolling text list of the boot processes (instead of the KITT" bar.

Also some goofd info for using USB in Linux:
[http://beastie.cs.ua.edu/cs150/configuration.html](http://beastie.cs.ua.edu/cs150/configuration.html)

---

### Post by KhurramM on 2009-05-20
Try altenate Cd instead of live CD for nongui installation.

If u r just booting, add nosplash or text in place of splash in the end of the line kernel:

in
/boot/grub/menu.lst

Hope this helps u

---

### Post by emarkay on 2009-05-20
I am booting fro a USB - there's no grub - just a straight boot - is there an "Autoexec" or something I can edit to set nosplash quiet?

---

### Post by reevine on 2009-05-21
There isa grub. you cant boot a system without a bootloader. its simply inside ubuntu.

---

