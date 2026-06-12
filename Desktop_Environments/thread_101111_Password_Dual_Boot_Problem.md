---
title: "Password Dual Boot Problem"
date: 2005-12-09
forum: Desktop Environments
---

### Post by Squishedlizard on 2005-12-09
Hi,

I did a dual boot of Ubuntu & Windows XP. I can choose the operating system just fine. I didn't give ubuntu a password, but when I try to login, it tells me my password is wrong. It won't accept any combination I can think of. None of my usual passwords, not admin, nothing. Uhm, does anybody know hpw to fix this? Thanks,
~Squishy

---

### Post by lisje on 2005-12-09
you could try booting a linux-cd, mount the ubuntu partitions and chroot into it, and change your passwd.... 

something like this:

mount the partitions:
```
# mount /dev/hda3 /mnt/ubuntu
# mkdir /mnt/ubuntu/boot 
# mount /dev/hda1 /mnt/ubuntu/boot
```

chroot into your ubuntu:
```
# chroot /mnt/ubuntu /bin/bash
```

changing your password:
```
# passwd <username>
```
make sure you change "<username>" by your own username

---

