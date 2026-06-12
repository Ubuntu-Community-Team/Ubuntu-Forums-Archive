---
title: "Removing Ubuntu"
date: 2008-12-15
forum: General Help
---

### Post by dethredic on 2008-12-15
I am currently duel booting ubuntu and vista, and I would like to remove Ubuntu. I don't want vista to disappear, so if I boot into my gparded CD, then format over ubuntu with NTFS will everything work, or will the destroyed grub not let me get into vista?

---

### Post by Titan8990 on 2008-12-15
You will have to restore the Vista MBR with a Windows install disc. The Vista install disc now actually comes with a wizard that will do this for you.

---

### Post by dethredic on 2008-12-15
alright, thanks.

Time to find that vista CD...

---

### Post by logos34 on 2008-12-15
if you can't find it let us know...there's a workaround

---

### Post by dethredic on 2008-12-15
> **logos34 said:**
> if you can't find it let us know...there's a workaround

Ok, that would be nice. My friend has my cd atm, and I won't be able to get it back till thursday.

---

### Post by logos34 on 2008-12-15
Before you're ready to delete ubuntu, boot into vista and download and install EasyBCD bootloader.  Then delete ubuntu partition, either from within vista or using gparted cd

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)
[http://neosmart.net/wiki/display/EBCD/Windows+Vista](http://neosmart.net/wiki/display/EBCD/Windows+Vista)
[http://neosmart.net/wiki/display/EBCD/Repairing+the+Windows+Vista+Bootloader](http://neosmart.net/wiki/display/EBCD/Repairing+the+Windows+Vista+Bootloader)

---

### Post by dethredic on 2008-12-16
Thanks, I will try this out tonight.

---

### Post by run1206 on 2008-12-16
> **dethredic said:**
> Thanks, I will try this out tonight.

if you don't me asking, any reason why you're removing Ubuntu for your Vista/Ubuntu partitions?  I ask because i just bought a new laptop and want to install Intrepid with my Vista Partition, but i'm iffy if anything goes wrong(i didn't receive a recovery CD with Vista) :(

thanks in advance

---

### Post by dethredic on 2008-12-16
> **run1206 said:**
> if you don't me asking, any reason why you're removing Ubuntu for your Vista/Ubuntu partitions?  I ask because i just bought a new laptop and want to install Intrepid with my Vista Partition, but i'm iffy if anything goes wrong(i didn't receive a recovery CD with Vista) :(

thanks in advance

Ok, that EasyBCD worked great, no problems.

I am removing Ubuntu because I am turning my rig into a dedicated gaming rig and throwing ubuntu on the laptop I will be getting for christmas. :)

---

