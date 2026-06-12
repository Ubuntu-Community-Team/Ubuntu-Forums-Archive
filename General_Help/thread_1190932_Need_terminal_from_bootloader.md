---
title: "Need terminal from bootloader"
date: 2009-06-18
forum: General Help
---

### Post by letmekilluplz on 2009-06-18
Ok I messed up my menu.lst and I need to access a terminal from the bootloader I can press "C" to get a grub shell but I can't get to my menu.lst. Worse I don't have my live cd or internet access

---

### Post by Brandon Williams on 2009-06-18
Almost anything that you can do by editing menu.lst can be done from a grub shell and/or the grub menu. You can probably make changes on-the-fly at boot time to get you back into a running system and then edit menu.lst.

What specific changes do you want to make to your menu.lst file? We can probably help you figure out how to do that at boot time so that you can boot into linux in order to edit menu.lst.

---

### Post by letmekilluplz on 2009-06-18
I went to comment out the options I dont need but apparently commented out the wrong ones so I just need to boot into ubuntu of access my menu.lst

---

### Post by Brandon Williams on 2009-06-19
If you simply commented out the important boot-time commands, then you can view your menu.lst from the grub command prompt to figure out what the require commands are. Here's an example session:
```
grub> find /boot/grub/menu.lst
 (hd0,1)

grub> root (hd0,1)

grub> cat /boot/grub/menu.lst
... scroll through file looking for recovery session detail ...

#title               Ubuntu 8.04.2, kernel 2.6.24-22-lpia (recovery mode)
#root                (hd0,1)
#kernel              /boot/vmlinuz-2.6.24-22-lpia ro root=UUID=af80216e-d9a4-45dd-9d54-ce4d7aaad6e3 acpi_osi=Linux hpet=disabled single
#initrd              /boot/initrd.img-2.6.24-22-lpia

... continue scrolling to end of file to get a new prompt ...
grub> 
```
Having found the details of the commented-out recovery mode commands, you can simply type them in at the grub prompt. After entering each of the required commands, enter the boot command, which should continue the boot into linux and bring you to a recovery mode console prompt, from which you can edit your menu.lst file.

---

