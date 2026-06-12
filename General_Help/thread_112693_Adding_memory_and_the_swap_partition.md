---
title: "Adding memory and the swap partition"
date: 2006-01-04
forum: General Help
---

### Post by jacrider on 2006-01-04
I installed Ubuntu 5.1 when I had 256MB of RAM.

I have since added another 512MB for a total of 758MB.

When doing the initial install, I let the partitioner set up the swap partion as it suggested, about 0.5GB, or twice the system RAM.

I am wondering if as a result of adding more memory I need to do anything about the swap.  Presumably with the increased memory, I need the swap less than before, so perhaps I don't need to do anything.

If I need to increase the size of the swap, how do I do that?  I don't want to re-install.  I can repartition anothter drive on my system for a new swap if necessary.

Thanks.

---

### Post by FizDev on 2006-01-04
Hi,
I might have an idea though I am not sure at all so you might want to backup your data! I think it would be possible to resize your swap partition by booting with the Ubuntu Install CD and selecting the partition utility and edit them manually. After that abort the install but save the disks modifications. It might be a little risky but you could try it.

Something else you could do is use the "fdisk" command... I wouldn't mess with it unless you know how to do it. Try googling "fdisk resize" maybe you'll find something.

Hope this helps!

---

### Post by professor_chaos on 2006-01-05
Do you currently use your swap? I often do intensive computations (and in matlab nontheless which is a real memory hog) and rarely use swap space.

---

### Post by jacrider on 2006-01-05
I have been checking the system monitor since adding the RAM, and rarely do I use over 400MB of my RAM (total 768MB) and as a result, don't touch the swap space.

My preference would be to not change anything as I don't really want to risk partitioning an active drive.  I am asking this question to make sure I am not going to run into problems in the future without more swap space.

Thanks.

---

### Post by magnusbb on 2006-01-05
Funny, I did the same thing yesterday - bought new memory, and thought of increasing the swap partition.

Well, as I didn't want to mess with my partition table, this is what I did:

**First create a swap file:**
sudo dd if=/dev/zero of=/swap_file bs=1M count=1000

You're free to change the location "/swap_file" and 1000 to whatever size you want.

**Then fix the permissions:**
sudo chown root:root /swap_file
sudo chmod 600 /swap_file

**Make it a valid swap file:**
sudo mkswap /swap_file

**The final thing we want to change is in /etc/fstab. Open this file and do the following:**

/dev/your_swap_partition         none            swap    sw   pri=1           0       0
/swap_file      none            swap    sw   pri=0           0       0

**Do a reboot.**

What happens now, is that, if you run out of swap space on you're partition, it will automatically switch to you're newly created swap file. This is done with the help of so-called swap priorities.

---

