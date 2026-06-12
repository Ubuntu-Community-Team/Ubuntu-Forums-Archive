---
title: "Ubuntu 8.10 no gui."
date: 2009-03-30
forum: General Help
---

### Post by clone11 on 2009-03-30
I'm hoping i'm not the only one that has had this problem, I recently installed Ubuntu 8.10 then I installed the nvidia drivers 177, Did the updates. Once I restarted the gui would not boot. I read on some other sites saying it was because of the wrong BusID for my cards. I tried running sudo nano /etc/x11/xorg.conf but the file is blank and when I try to save it it says it doesn't exist. I also tried sudo nvidia-xconfig no luck either. I have also tried doing dpkg-reconfigure xserver-xorg

Specs
2x Nvidia 9800GTX
E8400 Intel
2Gb DDR2 ram
Connected directly to the router.

---

### Post by Mike_IronFist on 2009-03-30
> **clone11 said:**
> I'm hoping i'm not the only one that has had this problem, I recently installed Ubuntu 8.10 then I installed the nvidia drivers 177, Did the updates. Once I restarted the gui would not boot. I read on some other sites saying it was because of the wrong BusID for my cards. I tried running sudo nano /etc/x11/xorg.conf but the file is blank and when I try to save it it says it doesn't exist. I also tried sudo nvidia-xconfig no luck either. I have also tried doing dpkg-reconfigure xserver-xorg

Specs
2x Nvidia 9800GTX
E8400 Intel
2Gb DDR2 ram
Connected directly to the router.

Have you tried booting using the recovery mode kernel?

---

### Post by clone11 on 2009-03-30
I tried booting to recovery mode still nothing drops me to the shell letting me enter my user and pass. I tried using Xfix and Dkpg on the recovery aswell it didn't do anything, I tried opening /etc/x11/xorg.conf and it still was blank

---

### Post by norwoods on 2009-03-30
if 2x Nvidia 9800GTX means you are running sli, search for nvidia sli and you will find that you have company.

---

### Post by clone11 on 2009-03-30
I tried uninstall the nvidia drivers. That worked my gui was restored so I tried to install the nviida drivers again... Same problem, it seems nvidia is not writing the etc/x11/xorg.conf file

---

### Post by briansvgs on 2009-03-30
Is there any output when x crashes? If so, what is it? Also, can you post your current xorg.conf?

---

### Post by clone11 on 2009-03-30
My current xorg file is blank, It pops up with a no screen error, I looked the problem up and I needed to change the busid, BUT there isn't anything in my xorg.conf file it's completly blank.

---

