---
title: "Error in compiling qemu-nightly on 8.10 and 9.04 i386"
date: 2008-12-10
forum: General Help
---

### Post by addiekaul on 2008-12-10
Hello All,

I am seeing error's while compiling qemu-snapshots on both intrepid and jaunty.

I installed gcc-3.4 on 8.10 and 9.04 as there is no gcc-3.3 available.

It works fine on hardy.


Thanks in Advance.

Addie


/home/ubuntu/qemu-snapshot-2008-12-10_05/linux-user/syscall.c:4676: error: dereferencing pointer to incomplete type
/home/ubuntu/qemu-snapshot-2008-12-10_05/linux-user/syscall.c:4677: error: dereferencing pointer to incomplete type
/home/ubuntu/qemu-snapshot-2008-12-10_05/linux-user/syscall.c:4678: error: dereferencing pointer to incomplete type
make[1]: *** [syscall.o] Error 1
make[1]: Leaving directory `/home/ubuntu/qemu-snapshot-2008-12-10_05/i386-linux-user'
make: *** [subdir-i386-linux-user] Error 2
ubuntu@ubuntu:~/qemu-snapshot-2008-12-10_05$

---

### Post by Titan8990 on 2008-12-10
9.04 does not exist yet.


Have you considered the qemu in the repositories?

---

### Post by addiekaul on 2008-12-10
Thanks for the reply.

I want to use e1000 as the NIC model which is not available in the qemu release in the repository.

I meant i tried in jaunty daily release.

Regards,
Addie

---

