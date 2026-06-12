---
title: "Hibernates, but Resume results as fresh boot"
date: 2009-03-06
forum: General Help
---

### Post by rowbird on 2009-03-06
Hi, I am Running Hardy on a Toshiba Laptop which was hibernating and resuming fine for weeks until one day, i noticed it would not hibernate anymore. I have a 2 gig swap partition, and 2 gigs RAM. I set up my fstab with /Dev/hda3/ instead of UUID. After, i noticed that the computer had assigned my swap partition a new incorrect UUID. After using "blkid" command i replaced it with the correct UUID and now it seems to hibernate, but it will not resume. It will just fresh boot when i start up the computer again. How can I tell if the image was written to the swap partition, and how does the computer know to resume? This problem has been plaguing me for some time now, and any help would be most appreciated. thanks

---

### Post by rowbird on 2009-03-07
Solved! I could tell it was writing to the swap because the hdd led was blinking the whole time while hibernating. The problem was with the "/etc/initramfs-tools/conf.d/resume". I ran "sudo blkid" and copied the UUID of my swap partition, then replaced the line in the above mention location that reads "RESUME=UUID=..." with the actual swap UUID.
   then i ran "sudo update-initramfs -u" to update my initrd with the correct UUID, and rebooted. Thats it Resume is back!

---

### Post by MastroOmbroj on 2009-03-08
> **rowbird said:**
> Solved! I could tell it was writing to the swap because the hdd led was blinking the whole time while hibernating. The problem was with the "/etc/initramfs-tools/conf.d/resume". I ran "sudo blkid" and copied the UUID of my swap partition, then replaced the line in the above mention location that reads "RESUME=UUID=..." with the actual swap UUID.
   then i ran "sudo update-initramfs -u" to update my initrd with the correct UUID, and rebooted. Thats it Resume is back!

Hi, I yesterday encounter same problem with my MSI Wind U100. After some swap partition manipulations and after system update I lost hibernation feature. Symptoms was the same: write to disk something, but boot as normal.

Thank you very much :D. This was exactly the problem I have too. Now its fixed.

---

