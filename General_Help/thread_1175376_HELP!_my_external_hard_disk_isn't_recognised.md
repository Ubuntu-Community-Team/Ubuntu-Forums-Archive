---
title: "HELP! my external hard disk isn't recognised"
date: 2009-06-01
forum: General Help
---

### Post by Chinedu on 2009-06-01
Jst recently, my ubuntu 8.04 displays 'device descriptor error' when i plug my 250g SATA hard disk. It started after i transferred some files from it to a windows machine. Pls how can i save my backup, it has my final year project. Pls help.

---

### Post by pastalavista on 2009-06-01
Plug in the drive and then post the output of these commands in terminal
```
sudo fdisk -l
```and```
sudo nano /etc/fstab
```

---

