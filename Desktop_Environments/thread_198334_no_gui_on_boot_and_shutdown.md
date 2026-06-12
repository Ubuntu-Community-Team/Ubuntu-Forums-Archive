---
title: "no gui on boot and shutdown"
date: 2006-06-17
forum: Desktop Environments
---

### Post by fr33mind on 2006-06-17
hi,

after playing withmy menu.lst from the grub bootloader i got an errorcode and fixed it with the livecd... since that i dont get the gui on boot and shutdown.. anyone know why? I dont get any relevant errors or warnings on boot/shutdown :(

thanks for help! :KS

---

### Post by x64Jimbo on 2006-06-17
Your menu.lst entries are probably missing the "splash" argument. Your kernel line should look something like this:
```
kernel        /boot/vmlinuz-2.6.15-25-amd64-generic root=/dev/sdb1 ro quiet splash
```

---

### Post by fr33mind on 2006-06-17
thank you very much! it worked :-) :D

---

