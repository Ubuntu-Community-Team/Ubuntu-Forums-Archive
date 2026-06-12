---
title: "scared to erase uneccecary 2nd ubuntu install"
date: 2006-03-25
forum: Desktop Environments
---

### Post by sharperguy on 2006-03-25
You see, i though i had killed ubuntu so oi reinstalled on a separate partition, however it overwrote the bootloader and since i fixed my old install i have no need for the 2nd one and i have to keep chossing the first one oin grub, and its using unesecary space on my drive.

So can anyone tell me how i can tell the bootloader to look on the main partition for menu.lst so when i erase the new partition it wont be all like "where the smurf is menu.lst??"

Cheers

---

### Post by aysiu on 2006-03-25
This should help:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

### Post by sharperguy on 2006-04-22
ok i followed this but killed windows in the preccess.

After doing some research i found the answer:

All you have to do is load your distro that you want to be the main booter (bad english there) and type:

Ubuntu:
```
sudo grub-install hda
```
NOT hda1!!!!!!

Other Distro:
```
su
<type password>
grub-install hda
```

---

