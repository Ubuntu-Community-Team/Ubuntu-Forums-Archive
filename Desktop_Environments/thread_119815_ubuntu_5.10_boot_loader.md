---
title: "ubuntu 5.10 boot loader"
date: 2006-01-20
forum: Desktop Environments
---

### Post by shawn_selig on 2006-01-20
hello.. i previously installed ubuntu 5.10 on my 2 partion with a ext 3 file format... i ran the setup cd and everything is on the partition except the boot loader.... i ran the setup disk and stopped it at the boot loader option.... so can anyone tell me how can i get this boot loader either on floppy or  hard drive... also i already got windows 98 se on it and want it setup to dual boot with ubuntu so i can select the different operating systems... thanks

---

### Post by shawn_selig on 2006-01-20
so, basically all i'm looking for is how to load up the boot loader for it..(i think its called gbr loader or something like that..either install the loader on floppy or hard drive, thanks

---

### Post by renzokuken on 2006-01-20
i guess your thinking of "grub" boot loader

if u already have win98 installed, then installing ubuntu will automatically create the grub boot loader for u during the installation, allowing u to choose between win98 and ubuntu when u start up the computer

---

### Post by shawn_selig on 2006-01-20
its called grub boot loader.. i believe... its the last step in the ubuntu instal i have to finish... if anyone has any stuff i can try to continue the install... without restarting the process.. i got up to everything except the grub loader installtion....but once it hit the grub boot loader installtion screen ... the power went out.. which interupted the process.. so i need to continue it without re-starting the process, any help will be appreciated..

---

### Post by Ocxic on 2006-01-20
go thru the install steps again like normal and when you hit the partitioning part, choose to manually edit the table and tell it not to format any partitions. then it will fail the base system install, ignore the error messages, and select install grub for the menu that comes up, that should get it working for you and should let you comlete the rest of the install, but if the power went out, i would reccomend that you just re-install anyway.

---

