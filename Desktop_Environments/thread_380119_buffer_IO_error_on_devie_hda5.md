---
title: "buffer I/O error on devie hda5"
date: 2007-03-09
forum: Desktop Environments
---

### Post by warlock_handler on 2007-03-09
buffer I/O error on devie hda5

this is what i get everytime when i start my comp... i cant understand why this is happening, also if there is something wrong with my HDD why does it show hda5 cause the uBuntu installation is on hda01 ie. my HDD what is hda5 represent??

---

### Post by chewearn on 2007-03-09
hda5 is the first logical partition inside the extended partition on the same drive.  I'm guessing you have single ubuntu installation (not dual boot); then the hda5 will be your swap partition.

---

### Post by warlock_handler on 2007-03-09
> **AstalaVista said:**
> hda5 is the first logical partition inside the extended partition on the same drive.  I'm guessing you have single ubuntu installation (not dual boot); then the hda5 will be your swap partition.

so if i get a buffer I/O error what does that signify? something wrong with my HDD??? or HDD bad sector?? or HDD crash...

---

### Post by warlock_handler on 2007-03-12
ok i figured what was wrong.. there were some bad sectors in the HDD and hence i was getting that error.. so what i did was formatted my HDD and this time while installing uBuntu i selected manually partition your HDD.... i put the root, /home, /urs, /boot, /var etc is different partitions i had made... and it really helped out.. ohh my suggestion whatever be your RAM create a SWAP partition that is atleast twice or three times more of that size..

---

