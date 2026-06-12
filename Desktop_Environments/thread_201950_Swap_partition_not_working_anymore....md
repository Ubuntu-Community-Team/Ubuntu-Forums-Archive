---
title: "Swap partition not working anymore..."
date: 2006-06-22
forum: Desktop Environments
---

### Post by JetaKing on 2006-06-22
For some reason, Ubuntu is not detecting my swap partition anymore (it has been working fine for weeks). When I go to the system monitor, my Used swap is at 0 bytes of 0 bytes... I'm not sure what I did, and I keep running out of memory. Does anyone have any ideas? :)

---

### Post by Ramses de Norre on 2006-06-22
Could you post the output of these commands: ```
cat /proc/swaps
cat /etc/fstab
sudo fdisk -l
```

---

