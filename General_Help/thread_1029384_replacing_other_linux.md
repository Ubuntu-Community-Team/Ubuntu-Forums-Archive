---
title: "replacing other linux"
date: 2009-01-03
forum: General Help
---

### Post by m005k on 2009-01-03
I have a dual boot WinXP with Suse 11. After my total failure to get the wifi working, I have decided to come back to Ubuntu where everything just works right "out of the box". I know, what was I thinking when I switched. I want to install Ubuntu and replace he other Linux. I did this once before and ended up with two linuxes.
Can I force Ubuntu to replace the other linux? will grub sill work correctly?
Mike

---

### Post by oldos2er on 2009-01-03
Use manual installation, point Ubuntu to the partition where OpenSuse is, and set it as /. If you already have a swap partition, Ubuntu should use it automatically--grub should update automatically too.

 Backup anything you don't want to lose.

---

### Post by mikjp on 2009-01-03
And now that you are reinstalling the system, remember to make a separate /home partition. It will make the next reinstall easier :-)

---

### Post by anjilslaire on 2009-01-03
> **mikjp said:**
> And now that you are reinstalling the system, remember to make a separate /home partition. It will make the next reinstall easier :-)

+1 for separate /home

---

### Post by m005k on 2009-01-03
Could you give me a little more detail about setting up he separate home partition?

Mike

---

### Post by CrusaderAD on 2009-01-03
When installing Ubuntu again, just make sure you selected to correct partition to install it to. If you format the partition, you should end up with one version of linux after the install... Ubuntu.

---

### Post by theozzlives on 2009-01-03
> **m005k said:**
> Could you give me a little more detail about setting up he separate home partition?

Mike

Just resize your / partition and create a new one. Set the mount point to /home, then finish the install.

---

### Post by mikeize on 2009-01-03
During install, mount /Home to a separate partition.

---

