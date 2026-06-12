---
title: "GRUB Loading Stage 1.5."
date: 2009-06-15
forum: General Help
---

### Post by zilu54 on 2009-06-15
I have a gateway laptop and installed with ubuntu and windows vista [dual boot]
once I lend my laptop to my mom for her purpose to chat in Yahoo Messenger in windows, in another day I open my laptop then I just encounter a problem, A black screen then only appears "GRUB Loading Stage 1.5." then that's all...it stuck on that process.

could you guys help me? is there any thing I could use it normally because I have a lot of files in windows and specially in ubuntu.

My laptop:
Gateway Laptop | Dual Boot (Windows Vista Home Professional / Ubuntu: Jaunty)

---

### Post by utnubuuser on 2009-06-16
A link:  [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351") - I've used  this technique and know it works.

Before you go through the steps though,  Use a live disk, open your ubuntu install's /boot/grub/menu.list and copy it to as /home/yourusername/Desktop/menu.list.backup in case recovering grub doesn't catch your windows partitions. ( Then you can copy from the backup file to the new menu.list file the info needed to launch windows.)

---

### Post by zilu54 on 2009-06-24
ok another problem...
the "GRUB Loading Stage 1.5." keeps returning anytime I use the windows vista partition.

how can I make it permanent to prevent this GRUB problem?

---

### Post by utnubuuser on 2009-06-24
Remove Vista from the hdd and welcome Linux exclusivity with any and all of it's  shortcomings?

---

### Post by zilu54 on 2009-06-26
> **utnubuuser said:**
> Remove Vista from the hdd and welcome Linux exclusivity with any and all of it's shortcomings?
 I just wanted too...
but still, use Vista for my mom because she only wants to chat using real yahoo messenger and another thing...I am still using photoshop as well since im not really good at gimp and it has some thing that it doesn't have in photoshop and vice versa.
 
I hope you guys can help me~

---

