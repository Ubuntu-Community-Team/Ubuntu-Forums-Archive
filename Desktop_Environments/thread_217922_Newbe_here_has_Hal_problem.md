---
title: "Newbe here has Hal problem"
date: 2006-07-17
forum: Desktop Environments
---

### Post by CaveRat on 2006-07-17
I downloaded the latest version of Ubuntu yesterday evening and ran it from the disk. I had no problems until I installed it. I am getting an internal error: "Failed to initialize Hal!" I also noticed since I installed, my card reader is not showing in Computer.

---

### Post by Gordon Farmer on 2006-07-17
I don't know much about Hal but when it wasn't working for me, my card reader was not recognized either.  I read somewhere that Hal needs the Linux kernel version 2.6 in order to function properly.  If you are using the Linux kernel version 2.4 it won't work.

When you boot up, and you get the Grub message with the functioning countdown timer, press the Escape key and make sure you are using a Linux kernel 2.6 and if you are using the 2.4 kernel, you can install the 'kernel' 2.6 using System > Administration > Synaptic Package Manager

Not sure this is your problem.

---

### Post by Sweezel on 2006-07-18
I have begun experiencing this "failed to initialize hal" error after adding a Samba share to my fstab file.

Other threads have shown this to be a problem for several months. If you search for this error in the forums, you will find some workarounds.

---

