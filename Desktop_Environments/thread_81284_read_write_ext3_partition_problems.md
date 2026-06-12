---
title: "read/ write ext3 partition problems"
date: 2005-10-24
forum: Desktop Environments
---

### Post by Stambo00 on 2005-10-24
I'm running a dual boot with both winodws xp and ubuntu breezy. I also have a DATA partition used to store files. Originally this was formatted with the ext3 filesystem. Recently, however, I formatted this DATA partition to FAT32 so i could use the free space to burn some dvds on my windows partition. After i finished burning my dvds i changed the DATA partition back to ext3. When booting back into breezy my partition is listed on the desktop but I am unable to read/ write as i no longer have permissions. I've been trying to change the permissions to "/dev/sda6" (my data partition) but nothing works. Should I be changing something in "/etc/fstab"?

---

### Post by Pablo_Escobar on 2005-10-24
Yep, fstab tells system what filesystem the partition uses. You need to check if the partition has vfat or ntfs entry.

---

### Post by Stambo00 on 2005-10-24
My ext/fstab is as follows "/dev/sda6       /media/sda6     ext3    defaults        0       2" What could i change?

---

### Post by Pablo_Escobar on 2005-10-24
Hmmmm, it looks fine for me, are You sure that sda6 partition is ext3 formatted ??
Check with gparted or some other tool.

---

### Post by Stambo00 on 2005-10-24
It seems i needed to change permissions for "media/sda6" rather than "dev/sda6". If i was to install a second breezy partition will i be able to share permissions between the "DATA" partition with the two ubuntu's?

---

### Post by Pablo_Escobar on 2005-10-24
Try this one - "sudo nautilus" in terminal, Go in nautilus to /media/, right click sda6, properties and check the permissions. 
But AFAIK fstab should do all the permissions.

---

### Post by Stambo00 on 2005-10-24
Thankyou for your help for my first official help post. It was extremely helpful. Everything works fine now.

---

### Post by Pablo_Escobar on 2005-10-24
Glad to be of service :) Cheers :D Glad it worked for You :)

---

