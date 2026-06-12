---
title: "fstab replace?"
date: 2006-04-05
forum: Desktop Environments
---

### Post by caviva on 2006-04-05
Hello,

i don't know how, but fstab is empty now...

i got a copy of it, but i can't write to /etc/

i can open the fstab, it's empty, i can't write. Anyone an easy solution? in fact it's just a question of copy paste, but i dont know how= Dont have the rights to change filenames or copy paste the backup file...

tx in advance

---

### Post by aysiu on 2006-04-05
I'm amazed you can even log in with an empty /etc/fstab.

Let's say, for this example, that your backup copy is called /etc/fstab_backup.

Go to a terminal (Applications > Accessories > Terminal) and type ```
sudo cp /etc/fstab_backup /etc/fstab
```

---

### Post by caviva on 2006-04-05
tx a lot=

yes it was a surprise..i was scarde to death..but ubuntu replaces it when booti ng... hope it's still there after reboot
tx=

---

