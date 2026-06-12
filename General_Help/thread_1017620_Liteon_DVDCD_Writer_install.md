---
title: "Liteon DVD/CD Writer install"
date: 2008-12-21
forum: General Help
---

### Post by Barry762 on 2008-12-21
Hi all, Today I bought a Liteon 20x DVD/CD Writer,  any help regards installation would be much appreciated (Dell Mini 9 Ubuntu) I have tried running the install disc, but it says... Error autorunning software. Error starting autorun program: Permission denied. There is however a CD image on the desktop and can be opened to display the various software files contained within. TIA

---

### Post by kg4tah on 2008-12-21
I have one and no install was necessary.  Ubuntu should pick it up automatically.  Are you attempting to install windows software from the disk?  If so don't.  DeVeDe is in the repo for burning dvd movies, Brasero disk burning comes with the default install of ubuntu which is good for burning data cd-r and dvd-r.

---

### Post by 73ckn797 on 2008-12-21
> **Barry762 said:**
> Hi all, Today I bought a Liteon 20x DVD/CD Writer,  any help regards installation would be much appreciated (Dell Mini 9 Ubuntu) I have tried running the install disc, but it says... Error autorunning software. Error starting autorun program: Permission denied. There is however a CD image on the desktop and can be opened to display the various software files contained within. TIA


If the system does recognize the drive then you could have a disk problem. I have had some disks just not read in different drives at times in the past. I also have had DVD and CD drives just not play well with my machine. That has been an issue with Windows and Ubuntu. 

My son runs Vista and could not burn any disks with a new drive I installed. I put back his other/old drive and the system burns perfectly. That same drive would not play well in my computer under Ubuntu or Windows XP. I thought that it was going bad.

---

### Post by Barry762 on 2008-12-21
My initial reason for buying it is to reinstall Ubuntu from disc. However when I press 0 on startup to get the boot options > select boot from dvd/cd > enter, Ubuntu just starts up as normal. This is why I thought the Liteon was not being recognised.

So basically if the Liteon is installed ok, how do I boot from it ?

---

### Post by polmir on 2008-12-21
Look for a file```
 /etc/udev/rules.d/70-persistent-cd.rules
```
In the name of the file may be different numbers.
Follow his backup, and then remove all of its contents. Save your changes and reboot the computer.

---

