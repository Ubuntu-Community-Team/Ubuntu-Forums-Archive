---
title: "Problem: Doesn't halt!"
date: 2006-06-03
forum: Desktop Environments
---

### Post by lotv on 2006-06-03
i use dapper, and my pc does not halt. When i do sudo halt, it finishes all the processes but stops at the "will now halt" stage so i have to turn the pc off manually...

i have the acpid acpi-support apmd stop-bootlogd scripts running too...

---

### Post by Haegin on 2006-06-21
I have the same problem? Is there a fix?

---

### Post by Genesius on 2006-06-21
Which kernel are you using? I've noticed that when I use the K7 kernel (I have a Duron processor) the same thing happens, but when I use the 386 kernel the system shuts down properly.

---

### Post by Genesius on 2006-06-21
Just got this response in the thread I had started about my power problem. Maybe it'll help you, too. 

> Be sure you enabled acpi in your BIOS and modify your /boot/grub/menu.lst and add apm=on and acpi=on so it looks like this

```
kernel /boot/vmlinuz-2.6.15-25-k7 root=/dev/hda8 ro quiet splash vga=775 apm=on acpi=on
```


if its still not working try
```
kernel /boot/vmlinuz-2.6.15-25-k7 root=/dev/hda8 ro quiet splash vga=775 apm=on acpi=force
```


This should solve your problem with shutdown.

---

