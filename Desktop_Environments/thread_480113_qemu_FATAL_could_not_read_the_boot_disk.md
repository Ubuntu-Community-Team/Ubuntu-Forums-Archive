---
title: "qemu FATAL: could not read the boot disk"
date: 2007-06-21
forum: Desktop Environments
---

### Post by GNUoob on 2007-06-21
anyone have any suggestions as to what i'm missing here?

dave@Darwin:~/Qemu_OS/win98$ qemu -a /home/dave/Qemu_OS/ -hda /home/dave/Qemu_OS/win98/w98hd.img -m 128 -a /home/dave/Qemu_OS/boot98.exe 
boot98.exe  win98/      
dave@Darwin:~/Qemu_OS/win98$ qemu -a /home/dave/Qemu_OS/boot98.exe -hda /home/dave/Qemu_OS/win98/w98hd.img
qemu: invalid option -- '-a'
dave@Darwin:~/Qemu_OS/win98$ qemu -fda /home/dave/Qemu_OS/boot98.exe -hda /home/dave/Qemu_OS/win98/w98hd.img
Could not open '/dev/kqemu' - QEMU acceleration layer not activated
dave@Darwin:~/Qemu_OS/win98$ 


help please

---

