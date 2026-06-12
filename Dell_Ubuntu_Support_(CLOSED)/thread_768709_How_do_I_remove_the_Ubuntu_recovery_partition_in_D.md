---
title: "How do I remove the Ubuntu recovery partition in Dell 1420N from within Ubuntu?"
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bcasanov on 2008-04-26
Hi, 

I would like to remove the Feisty recovery partition that came with my Dell 1420N originally.  I would like to do that within Nautilus, if at all possible.  Is there a way to do it?

---

### Post by ibutho on 2008-04-26
You could probably do this using partitioning tools such as gparted (should be listed somewere in the system menu).

---

### Post by bcasanov on 2008-04-26
How is the partition identified in gparted?

---

### Post by ibutho on 2008-04-26
> **bcasanov said:**
> How is the partition identified in gparted?
I don't own a dell laptop so can't be specific. On my maxdata laptop, its an NTFS partition.

---

### Post by bcasanov on 2008-04-26
Hi, here I have attached a screenshot of what appears on gparted, so that could maybe help.

---

### Post by ibutho on 2008-04-26
It seems like on your system, the rescue partitions are FAT (/dev/sda1 and /dev/sda2). I am not sure whether its normal for DELL to use two partitions for the rescue files.

---

### Post by bcasanov on 2008-04-26
Do you think the partition with the larger space is the recovery partition?

---

### Post by neptho on 2008-04-26
Leave the FAT16 partition alone; that's the diagnostic partition.  You may safely remove /dev/sda2 if you choose.

---

### Post by bcasanov on 2008-04-26
Thank you!  I think I'll go ahead and delete the /dev/sd2 partition, which might just be the recovery partition.

---

### Post by bcasanov on 2008-04-26
Okay, I deleted the partition.  This screenshot is the result of what shows up in Gparted.  I would like to merge this unused space back into my main / partition.  How do I do that?

---

### Post by bcasanov on 2008-04-26
Is it necessary to resize the /dev/sda6 partition?

---

### Post by gbrainin on 2008-04-26
I'm pretty sure that gparted won't let you make changes to partitions that are mounted.  If you want to make changes to your linux partitions, the easiest way is to run gparted from the live CD.

---

### Post by neptho on 2008-04-27
You'll have to do it from the live CD.  First, you'll have to add the space to your primary partition, then add it to whatever errxtended partition you wish.

---

### Post by chem199 on 2008-04-29
You can run "sudo umount /dev/sda2" that is the back up partition. but i recommend leaving it, it makes reinstall a breeze, incase there was a mistake with an upgrade and it is only 5Gbs so it is not like you're getting that much space. If you plan on keeping ubuntu on your dell, then you should prob keep it.

---

### Post by notwen on 2008-04-29
You may want to wait until Dell releases it's custom image for the Inspiron 1420n.  You can use this custom image to wipe all current partitions and setup your own before installing Hardy.  I currently am running the custom Gutsy image and carry it around in my laptops bag in case a restore is needed on the go.

---

