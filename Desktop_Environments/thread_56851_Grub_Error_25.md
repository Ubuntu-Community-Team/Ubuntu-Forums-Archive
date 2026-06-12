---
title: "Grub Error 25"
date: 2005-08-14
forum: Desktop Environments
---

### Post by DiMaG on 2005-08-14
I installed kubuntu 5.04 to another computer. 
Primary IDE: master: Seagate 60.0 GB(Windows XP Professional)
                     slave: : Seagate 40.0 GB(for linux)
Secondary IDE: master: Toshiba DVD/CD-R
                          slave  : empty

After first step of installing, installation program says, that I must restart. After computer restarts, following message appears:

GRUB loading stage1.5.

GRUB loading please wait...
Error 25

OK, I know, that there is an other messages with these problems, but only thing, I understood, is switching HD's and re-installing, but it didn't work. Because only experience I have is reading old SOT-linux manual(1998) , I haven't got any ideas, what to do. Can anyone explain to me step-by-step and clearly, how to solve the problem.

---

### Post by tonysathre on 2005-08-15
did u install grub on the MBR...it could be an error in your menu.lst file... post it and see if someone with more knowledge than me can take a look at it for you...another things you could try is booting to the cd and reinstalling just grub

---

### Post by DiMaG on 2005-08-16
What command I must give to install just GRUB? And how I can get menu.lst without Linux? I tought, that Windows can't understand ext3 format. The problem is, that I'm **totally** new in Linux. So I need the **simple** way.

---

### Post by tonysathre on 2005-08-16
sorry i misunderstood, to just install grub put the cd in and boot to it, let it configure and stuff then when it gets to the partitioning part go back and go down til u see install grub

---

