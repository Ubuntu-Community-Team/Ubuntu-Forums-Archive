---
title: "Dell vostro 1510"
date: 2009-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vaibhav vijay on 2009-05-19
I have dell vostro 1510 ..
keypad & touchpad is not working in ubuntu 9.04...
so plz help me:guitar:

---

### Post by techrush on 2009-05-19
its this bug: [https://bugs.launchpad.net/ubuntu/+bug/334249](https://bugs.launchpad.net/ubuntu/+bug/334249)

the solution for me and most other people was to edit /boot/grub/menu.lst
my working entry looks like this:

title           Ubuntu 9.04, kernel 2.6.28-12-generic
uuid            d655bf5b-3061-44bb-a9d8-2d6d9b4afc57
kernel          /boot/vmlinuz-2.6.28-12-generic root=UUID=d655bf5b 3061-44bb-a9d8-2d6d9b4afc57 ro quiet splash i8042.reset
initrd          /boot/initrd.img-2.6.28-12-generic
quiet


the key part is i8042.reset at the end of the kernel line for whatever kernel you are using.

---

### Post by anotherlinuxnewbie on 2009-07-18
> **techrush said:**
> its this bug: [https://bugs.launchpad.net/ubuntu/+bug/334249](https://bugs.launchpad.net/ubuntu/+bug/334249)

the solution for me and most other people was to edit /boot/grub/menu.lst
my working entry looks like this:

title           Ubuntu 9.04, kernel 2.6.28-12-generic
uuid            d655bf5b-3061-44bb-a9d8-2d6d9b4afc57
kernel          /boot/vmlinuz-2.6.28-12-generic root=UUID=d655bf5b 3061-44bb-a9d8-2d6d9b4afc57 ro quiet splash i8042.reset
initrd          /boot/initrd.img-2.6.28-12-generic
quiet


the key part is i8042.reset at the end of the kernel line for whatever kernel you are using.

That was it!  Great!  Thank you

---

