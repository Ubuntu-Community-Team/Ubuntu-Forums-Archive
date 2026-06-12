---
title: "686 Will Not Boot"
date: 2006-06-25
forum: Desktop Environments
---

### Post by markfasano on 2006-06-25
I have both Ubuntu 686 and 386 kernels and Windows installed on a Dell Dimension 8300 desktop. After cruising through the Dell BIOS screen, the GRUB loader turns up as normal. However, 686 will not boot for love nor money. Selecting 686 simply kicks the computer back to Dell BIOS, and so on ad infinitum. 686 in Recovery Mode does the same thing. But 386 boots up just fine. 

Anyone know what's going on?

---

### Post by evilghost on 2006-06-25
Weird, I've got two 400SC's that will boot Dapper without issue and the 400SC is the small business version of the 8300, I believe they share the same motherboard and Intel i875p Canterwood North Bridge.  What kind of processor do you have in there?  Have you tried 686-SMP if you have a Hyperthreading processor in there?  Running the latest BIOS?

---

### Post by markfasano on 2006-06-25
The BIOS is recently updated (BIOS 7 I think is Dell's latest). The processor is an Intel P4, but my limited understanding of symmetric multiprocessing is that it is for multiple processor systems. i.e. servers and duo-core Intel boards.

---

### Post by evilghost on 2006-06-25
If your processor is HT capable you should be using SMP but I see no reason why 686 won't boot and 686-SMP would...but it may be worth a shot.

---

### Post by mazelado on 2006-07-10
I had the same problem where the 386 kernel worked fine but the 686 kernel did not. Apparently ACPI was causing the problem. Edit your /boot/grub/menu.lst to add 'acpi=off' to your 686 kernel listing. Mine looks like this now:

```
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hdb1 ro acpi=off quiet splash
```

You can also change the defaults so that any future kernel updates will have this option by adding 'acpi=off' to this line which is also in /boot/grub/menu.lst:

```
# defoptions=acpi=off quiet splash
```

---

### Post by gadean on 2006-07-18
Thanks, mazelado!  This helped.

---

