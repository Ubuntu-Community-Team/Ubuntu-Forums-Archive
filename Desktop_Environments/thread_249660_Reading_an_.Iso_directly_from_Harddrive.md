---
title: "Reading an .Iso directly from Harddrive?"
date: 2006-09-02
forum: Desktop Environments
---

### Post by rolfotto on 2006-09-02
Is there a way to read an .iso file directly from the hard drive in Linux?

In Windows, I use a program called Alcohol 120% that creates a virtual drives and automatically mounts it.  Is there a linux equivalent?

---

### Post by taurus on 2006-09-02
Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo mkdir /mnt/iso
sudo mount -t iso9660 <filename>.iso /mnt/iso
cd /mnt/iso
ls -la 

```

---

### Post by taurus on 2006-09-02
Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo mkdir /mnt/iso
sudo mount -t iso9660 <filename>.iso /mnt/iso
cd /mnt/iso
ls -la 

```

---

### Post by rolfotto on 2006-09-03
Thanks for the help, I just run into problems mounting (2nd command) with the error message:

mount: name.iso is not a block device (maybe try `-o loop'?)

---

### Post by pufuwozu on 2006-09-03
Do:```
sudo mount -o loop -t iso9660 <filename>.iso /mnt/iso
```Instead.

---

### Post by rolfotto on 2006-09-08
Thanks pufowozu!

Worked perfectly.  Thanks again for the help.  I feel embarrassed for not knowing this, god knows that I mounted/dismounted enough drives before Ubuntu came along and did it automatically for me.... didn't even think that it was possible for an already mounted hard disk:D

---

