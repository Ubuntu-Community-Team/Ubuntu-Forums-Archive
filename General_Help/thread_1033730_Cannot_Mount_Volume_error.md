---
title: "Cannot Mount Volume error"
date: 2009-01-07
forum: General Help
---

### Post by mysn239 on 2009-01-07
I need to install my extra hardrive and its called "Extra storage"

It says i should safely hardware remove it from windows, but i don't have windows right now. so what do i do?

---

### Post by Michael.Godawski on 2009-01-07
hi, 
you could try to force mount the device.

Can you please post the output of these terminal commands, while your storage you want to mount is plugged in:

```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by Elfy on 2009-01-07
Does it not give you the syntax to force mount it in the error? I thought it did.

---

