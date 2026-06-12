---
title: "How to write an .img file to a floppy using dd?"
date: 2009-03-21
forum: General Help
---

### Post by dragos240 on 2009-03-21
Hello, i want to write an image file to a floppy using dd, it's a usb floppy drive and it's /dev/sdb1

---

### Post by Bachstelze on 2009-03-21
```
sudo dd if=image.img of=/dev/sdb1
```

---

### Post by dragos240 on 2009-03-21
> **HymnToLife said:**
> ```
sudo dd if=image.img of=/dev/sdb1
```

Hmm, i can't seem to boot from it though, and the floppy isn't mounting automaticly, i have to do it manually with -o loop. Help?

---

### Post by Bachstelze on 2009-03-21
My bad

```
sudo dd if=image.img of=/dev/sdb
```

If that still doesn't work, unplug the drive, plug it back, and paste the output of

```
dmesg | tail
```

---

