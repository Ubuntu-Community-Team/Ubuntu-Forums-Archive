---
title: "Saving OS configuration"
date: 2011-01-31
forum: Desktop Environments
---

### Post by Ricalsin on 2011-01-31
In MS Windows, I used a program to re-image my hard drive.  It was a great way to keep my OS configurations backed up in case of trouble.  Linux is more stable, but I'm capable of doing more damage to it.  So is there a good way to re-image this HD?  I don't see the old MS program (Acronis) for Linux.  Or, is there a way to save all of the synaptic programs I have downloaded so that I could more easily reload them if needed?

---

### Post by dashnak on 2011-01-31
If you want to image the drive you could try with clonezilla, and this command gives you a list of the packages you have installed:
```
dpkg --get-selections | awk '$2 ~ /^install$/ {print $1}' > list.txt
```

---

