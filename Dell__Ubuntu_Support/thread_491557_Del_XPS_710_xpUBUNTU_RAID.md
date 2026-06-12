---
title: "Del XPS 710 xp/UBUNTU RAID"
date: 2007-07-03
forum: Dell  Ubuntu Support
---

### Post by sdhog2002 on 2007-07-03
Hi all,
I take delivery today of an XPS 710 with RAID1. I wish to add a ubuntu partition. Will the Dell hardware RAID as delivered be supported in ubuntu? I have checked the Dell site and I cannot find a clear answer.

---

### Post by sr20ve on 2007-07-03
What kind of raid controller is it?

---

### Post by sdhog2002 on 2007-07-04
This is what is unclear to me. From the XPS documentation, it appears to be BIOS controlled RAID. Or software controlled through nVidia. I would have thought however, from the build options, that it has SATA hardware controlled RAID. My question (posted here and on Dell Community) is to find out if anyone knows what the setup is before I get the machine so that I can be prepared to set it up correctly.

---

### Post by neptho on 2007-07-04
You might try going into the BIOS and looking for settings, there.  It's likely a hardware RAID.  If so, and it's a JBOD or RAID0/RAID1 you likely won't have any problems changing the partitioning scheme.

---

### Post by sdhog2002 on 2007-07-05
Thank you neptho,
I have the machine and it does seem to be hardware RAID. I am going to try and install ubuntu this weekend.

---

