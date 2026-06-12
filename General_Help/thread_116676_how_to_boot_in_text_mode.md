---
title: "how to boot in text mode ?"
date: 2006-01-13
forum: General Help
---

### Post by bags on 2006-01-13
hy! :D 
while ubuntu is booting there is always an image at the bottom of the screen; do you know how to delete it and come back to an only text mode boot?
thanks, matteo :rolleyes:

---

### Post by bags on 2006-01-13
> title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash i8042.nomux=1 vga=0x305
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

i tried to remove "splash" and it boots in text-mode! i didn't think it was so stupid :D

---

### Post by mvaniersel on 2006-01-13
which configuration file is that?

---

### Post by bags on 2006-01-13
[QUOTE=mvaniersel]which configuration file is that?[/QUOTE]

/boot/grub/menu.lst
sorry i forgot to write the file name ;)

---

### Post by mvaniersel on 2006-01-13
thanks, I suspected something like that but I was looking for /etc/grub... ](*,)

---

### Post by bags on 2006-01-13
i discovered that if you remove "quiet" from the same line you can have a verbose boot ;)

---

