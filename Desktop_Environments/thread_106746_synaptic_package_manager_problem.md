---
title: "synaptic package manager problem"
date: 2005-12-21
forum: Desktop Environments
---

### Post by adil_mughal on 2005-12-21
Hi, I recently installed "Ubuntu Linux 5.04 : The Hoary Hedgehog Release" from a CD.  
However whenever I try to install a package using the synaptic package manager, I get the following message:

Please insert the disk labeled:
Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)
in drive /cdrom/

I have a working internet connection, I assumed the synaptic package manager would be downloading the package, and since I no longer have a copy of the CD, I then get the message

W: Failed to fetch cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/pool/main/g/gcc-3.3/gcc-3.3_3.3.5-8ubuntu2_i386.deb

I am a complete novice to Linux and Ubuntu in general, so any detailed advice would be greatly appreaciated. Thank you in advance.

---

### Post by rjwood on 2005-12-21
you can go into your sources.list file and comment (#) out the top line I thik it is asking for the cd. The first place the system is looking is in the cd. Good luck!!

---

### Post by adil_mughal on 2005-12-21
Yes that worked!! Thank you (and I learned something in the process too!!)

---

