---
title: "[SOLVED] where are backup files stored?"
date: 2008-12-08
forum: General Help
---

### Post by abhilashm86 on 2008-12-08
where will back up files stored,when we make a back up in terminal,where are files saved,can u tell me the path?

---

### Post by linux_tech on 2008-12-08
what command are you using to make the backup?

---

### Post by linux_tech on 2008-12-08
Most backup commands you specify source, what you want to copy 
to destination (where you want to place the copy)
ie.
diff-backup [options] <source> <target>

---

### Post by abhilashm86 on 2008-12-08
> **linux_tech said:**
> Most backup commands you specify source, what you want to copy 
to destination (where you want to place the copy)
ie.
diff-backup [options] <source> <target>

i had made a backup of GRUB menu.lst,so i wanted to view the original one

---

### Post by Sicaine on 2008-12-08
> **abhilashm86 said:**
> i had made a backup of GRUB menu.lst,so i wanted to view the original one

What is the command you used for backing up menu.lst?

Most time it is in the same folder with a extenstion like menu.lst.bak

---

### Post by abhilashm86 on 2008-12-08
its fine friends,i downloaded from net and repaired my grub menu.lst,yesterday i made some crap bootsplash images and ended not booting up ubuntu,then went to recover mode and altered,so the ubuntu is best os,cheers ubuntu linux!!!!!!

---

### Post by linux_tech on 2008-12-08
> **Sicaine said:**
> What is the command you used for backing up menu.lst?

Most time it is in the same folder with a extenstion like menu.lst.bak

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

---

