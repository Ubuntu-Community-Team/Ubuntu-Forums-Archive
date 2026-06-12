---
title: "[SOLVED] Combine /boot with /"
date: 2008-12-14
forum: General Help
---

### Post by plr4ever on 2008-12-14
When i first installed Ubuntu, i had seperate /boot and / directories. However, i want to combine them both together. Does anyone know how to do this?

---

### Post by kpkeerthi on 2008-12-14
1. Copy the contents from /boot to a temp folder /tempboot
```

sudo mkdir /tempboot
sudo rsync -a /boot /tempboot

```
* verify & set the permissions on /tempboot same as /boot

2. Comment the /boot mount line in /etc/fstab

3. unmount /boot
```
sudo umount /boot
```

4. Rename /tempboot to /boot

EDIT:
5. Update the root and kernel lines in /boot/grub/menu.lst. It should point to where / is.

**Reboot**

---

### Post by plr4ever on 2008-12-15
Perfect, thanks!

---

