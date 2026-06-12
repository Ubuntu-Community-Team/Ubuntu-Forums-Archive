---
title: "GRUB growing pains"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Trurl on 2006-07-17
Hi everyone,
  
   I've got an Ubuntu/XP dual boot and over time I have noticed that GRUB seems to collect duplicate listings for Ubuntu. I now how 8 options upon start up, with 3 pairs of Ubuntu/Ubuntu Recovery Mode, 1 instance of Memtest, and then XP. What does it mean that I have three identical pairs of listings for Ubuntu? How do I get rid of the redundant cases? What I have noticed is that they seem to appear whenever important system updates are installed. 

Thanks for any help.

-Trurl

---

### Post by DeadEyes on 2006-07-17
Are your sure they are duplicate listings? Look at the kernal versions closely, I think you'll find that after each kernal upgrade a new options is added.
You can edit /boot/grub/menu.lst and comment out the ones you don't want to see.

---

### Post by grim1234 on 2006-07-17
you'll have to reinstall grub after by using 'sudo grub-install' command too.

As above poster said it's probably new kernel versions (2 entries per kernel).

---

### Post by mcduck on 2006-07-17
> **grim1234 said:**
> you'll have to reinstall grub after by using 'sudo grub-install' command too.

As above poster said it's probably new kernel versions (2 entries per kernel).

No, there's no need for that. Grub doesn't need reinstalling after editing settings.

To get rid of those entries just uninstall older kernel versions with apt-get/Synaptic. This also removes entries from Grub menu.

(you could also just remove the entries from Grub, but why keep those files wasting your deskspace, as they are completely useless without entries in Grub to boot them..)

---

### Post by razorsmile on 2006-07-18
I would also like to edit my grub list to **add** a listing for dyne-bolic...the listing is given in the dyne folders and I know that I need to ensure it points to the right disk etc but I was wondering whether it's possible to simply add a listing to the file in /boot/grub/menu.lst or whether I then need to do something else...

---

