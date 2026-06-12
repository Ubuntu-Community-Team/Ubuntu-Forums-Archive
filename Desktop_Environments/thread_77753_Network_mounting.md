---
title: "Network mounting"
date: 2005-10-17
forum: Desktop Environments
---

### Post by zez on 2005-10-17
What is a good program for gnome that is similar to smb4k?  Browsing with Nautilus doesn't suit my needs and I want to be able to mount and unmount easily.

---

### Post by zez on 2005-10-17
Never mind, I forgot about LinNeighborhood. Working perfectly!

---

### Post by lonetree on 2005-10-20
but LinNeighborhood must be run as root in order to mount network drive, is there a way to make it run as normal use and yet able to mount? Just a thought.

Regards,

---

### Post by zez on 2005-10-20
You can chmod +s smbmount and smbumount and it works.

---

### Post by lonetree on 2005-10-21
Thanks Zez

but I still get error after changing /usr/lib/sambmount and smbumount.

Error :

SMB connection failed
libsmb base program must *NOT* be setuid root

what else do I have to change?

Thanks

---

### Post by zez on 2005-10-24
You should chmod +s /usr/bin/smbmnt and /usr/bin/smbumount NOT smbmount.

---

