---
title: "Partition Question?"
date: 2009-06-19
forum: General Help
---

### Post by cottfcfan on 2009-06-19
I have a 500gb hard drive with Ubuntu on SDA1 & Swap on SDA5 in a 5 Gig extended partion.
 I have created  200gb free space from SDA1 which I now want to fill with the extended partion to keep all my data on.
 My questions are, do i need to delete swap before I can extend my extended partition? Can I extend to the left? and will any data on the extended partition be visible from ubuntu on SDA1, or will I have to mount the extended partition every time to access the data?
Thanx in advance.

---

### Post by redilyn on 2009-06-19
You can resize the extended partition to the left without deleting swap (you WILL have to turn swap off from the livecd before you do this).

Then you can create a new partition in the free space of the extended partition. All data on the new partition will be visible. You will need to mount the new partition manually at each boot or add the new partition to fstab.

---

### Post by cottfcfan on 2009-06-19
Thanx Redilyn,
Will try it when I get home.

---

