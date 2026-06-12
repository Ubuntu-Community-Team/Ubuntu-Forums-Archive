---
title: "What's Ubuntu's Kernel"
date: 2007-05-24
forum: Desktop Environments
---

### Post by Loki1989 on 2007-05-24
I can tfind what kernal is currently in 7.04 and I need the number to boot. I think it is 2.6.21 but I am not sure.

---

### Post by Swab on 2007-05-24
For me it's 2.6.20-15-generic

---

### Post by Loki1989 on 2007-05-24
thanks man I need that ... I have vista installed and my new computer has some thing where it doesn't boot Grub but straight into the vista bootloader. I have a program that adds a grub command to the vista one and am working on it right now.

---

### Post by Swab on 2007-05-24
```

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=c2b40cea-d822-4024-9199-65f1316b7d3f ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

Obviously your root partition might be elsewhere.

---

### Post by NikoC on 2007-05-24
> **Loki1989 said:**
> I can tfind what kernal is currently in 7.04 and I need the number to boot. I think it is 2.6.21 but I am not sure.

In a terminal type ```
uname -r
```

---

### Post by mdwuznik on 2007-05-24
uname -r is fairly hard to type _before_ booting...

Michal

---

