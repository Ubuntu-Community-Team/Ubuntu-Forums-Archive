---
title: "Ubuntu 5.10 windows Xp and Vista"
date: 2006-06-05
forum: Desktop Environments
---

### Post by bigguy on 2006-06-05
can I triple boot these 3 with no problems. ???

---

### Post by codypumper on 2006-06-05
It depends on your pc and linux knowledge. What hard drive(s) do you have?

---

### Post by bigguy on 2006-06-05
I have one harddrive partioned twice, once for my main install of Xp pro and once for Vista. 1 120 gig hard drive.

---

### Post by rado_london on 2006-06-05
You have to give us more info about the partitions. Can you please give use the output of:
```
sudo fdisk -l
```
This will list the partitions with their correct details needed for someone to help you out.

---

### Post by bigguy on 2006-06-05
I don`t have ubuntu installed. I have one 120 gig harddrive. One partition is 20 gig and the other is 100 gig. Can I add ubuntu to this, or will Vista get in the way. They are both ntfs if that helps.

[QUOTE=rado_london]You have to give us more info about the partitions. Can you please give use the output of:
```
sudo fdisk -l
```
This will list the partitions with their correct details needed for someone to help you out.[/QUOTE]

---

### Post by codypumper on 2006-06-05
You should be good...I do reccomend you double check the steps of the installation and plan head, then double check your plans.

---

### Post by rado_london on 2006-06-05
Sorry for giving a bad advice

---

### Post by bigguy on 2006-06-05
thats no problem at al I should have been a bit clearer as well.

---

### Post by flip314 on 2006-06-06
Vista uses a different boot method than XP/2000.  That's why you have to install XP/2000 FIRST if you want to dual boot.  I'm not sure what level of support GRUB has for this new boot method.

Be sure you know what you're doing before you start!  I don't have any experience dual-booting it, as I completely removed every trace of Vista after about 2 hours of using it.

There's some HOWTOs on the net if you search around, I'd definitely check that out.  It's a lot easier than trying to fix your computer when Vista won't boot.

---

