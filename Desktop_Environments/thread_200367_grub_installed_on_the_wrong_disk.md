---
title: "grub installed on the wrong disk"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Vlatko on 2006-06-20
i have a sata disk which has 3 partitions. 2 ntfs for xp and one for linux. i also have a 120gb ide drive on which i store all my personal and really important stuff. 

now when the installer asked whether to install the grub on the master boot record of the first disk i figured it was going to install on the sata disk where my windows are located. but it installed on the ide drive which contains no os whatsoever, only personal stuff. this proabaly because ide drives are always numerated before sata in bios. 

anyhow the installation was succesful and i can boot both xp and kubuntu. but only if i re-arrange the boot order in bios so the ide drive is first and sata second. that way i can boot to both xp and kubuntu. 

so that definetly means the grub was installed on the wrong disk. i don't like to touch the ide drive which serves me as a back up disk so i am going to re-install kubuntu only this time i'm going to unplug the ide drive untill installation completes. 

so i would like to remove the grub from the ide drive which contains no os, can anyone show me how to do that?

thanks!

---

### Post by Vlatko on 2006-06-20
erm..anyone? :D

---

