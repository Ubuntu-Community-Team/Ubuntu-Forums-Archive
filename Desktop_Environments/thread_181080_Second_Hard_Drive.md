---
title: "Second Hard Drive?"
date: 2006-05-23
forum: Desktop Environments
---

### Post by fvs on 2006-05-23
I just installed Ubunto on my spare 20 gig WD hd (Slave) I didn't know how to install it so I disconnected my 80 gig seagate (master) and install it. Now I'm going to connect my (Master) back which has Fedora 5 on it. My question is how do I set up Grub to recognize Ubunto (Slave) drive?:confused:

---

### Post by Ramses de Norre on 2006-05-23
When you've got no seperate /boot partition (and I assume you don't)
This is my grub entry (without any boot options):
```
title           Ubuntu, kernel 2.6.12-10-k7
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot

```

You may need to change the kernel to 2.6.12-9-386 (the one that came on my install cd) or 2.6.12-10-386. Check in /boot to be sure (you can browse it from fedora).

---

