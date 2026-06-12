---
title: "more ntfs problems"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Hairy_Palms on 2005-10-15
k i did a clean install of breezy over my old hoary and was pleasently surprised that it automounts my ntfs partition which hoary didnt till i edited fstab but i got a problem in that i cant even read it unless im root i tried to change permissions but it says i cant change the permissions ofa read only a disk, i just want to be able to read from it as a user :( any ideas on fstab editting etc?

its fstab line is this
/dev/hdc1       /media/windows  ntfs    defaults        0       0

---

### Post by mrmcctt on 2005-10-15
Try [this link.]("http://ubuntuguide.org/#automountntfs")  It's from the Ubuntu guide and steps you through this pretty much step by step.

Hope this helps

---

### Post by Hairy_Palms on 2005-10-15
hmmm nope didnt work it still claims that normal user cant read it

---

### Post by piggyaugu on 2005-10-15
[QUOTE=Hairy_Palms]hmmm nope didnt work it still claims that normal user cant read it[/QUOTE]


make sure that you have this **umask=000** for the ntfs partition.

and **UMOUNT** before mount -a

normally it works

---

### Post by mrmcctt on 2005-10-15
Forgive me if I'm writing something stupid here but I noticed that *your* fstab says windows was on hdc1.

Did you copy and paste from the user guide or did you change the user guide commands to match your hdc1 windows mount?

---

### Post by Hairy_Palms on 2005-10-15
cheers everyone changing umask to 000 fixed it fine :D

---

### Post by Hairy_Palms on 2005-10-15
oh and does anyone know how to get the address bar back to normal in nautilus instead of the tabs?

---

### Post by brockjudkins on 2005-10-15
I was curious too, and found this:

[http://ubuntuforums.org/showthread.php?t=76296]("http://ubuntuforums.org/showthread.php?t=76296")

---

