---
title: "Dual Boot"
date: 2006-01-18
forum: Desktop Environments
---

### Post by WierdKid on 2006-01-18
Ta Da, Here I am. Sorry. Anyway. I'm having a horrid time with making this dual boot thing work properly. I have 2 hard drives in my computer. For the last few months I'd been running Windows XP. It booted from hdb, a 40 gig slave drive. After looking around a bit I decided to install Ubuntu. So I downloaded the ISO, burned it to a disk, and installed it to hda, a 80 gig master drive. I've gotten Ubuntu working to where I can run the internet from it and a few other simple things. But I can't boot Windows anymore. And I can't access the slave drive to rescue my files and format it. I'm not ready to give up windows just yet. And I need to keep the files on the slave drive. Does anybody have an idea on what I should do.

---

### Post by aysiu on 2006-01-18
I don't know if I can help, but *someone* can if you post the output of these two commands: ```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

