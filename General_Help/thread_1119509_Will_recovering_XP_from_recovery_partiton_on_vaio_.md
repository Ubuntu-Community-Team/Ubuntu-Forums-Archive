---
title: "Will recovering XP from recovery partiton on vaio erase Ubuntu?"
date: 2009-04-08
forum: General Help
---

### Post by nimonika on 2009-04-08
It seems in order to get back windows, I will have to go through the recovery partition and reinstall XP. I wanted to know if doing this will erase my ubuntu partition and then will I have to install ubuntu again. I can deal with getting grub menuloader back if that disappears, but I do not want to install ubuntu, yet again.

---

### Post by maheshasolkar on 2009-04-08
I've used Sony's recovery tool before, although on a laptop that did not dual-boot. From what I remember, it does not give any options on partitioning. It just restores the computer to the state it was when you bought it.

I would like to hear what your experience is.

---

### Post by mb_webguy on 2009-04-08
+1

Recovery partitions restore the computer to its original state, so unless that original state included an Ubuntu installation, The Ubuntu partition will be overwritten.

---

### Post by lisati on 2009-04-08
My experience on a Compaq machine (using a recovery partition) and a Toshiba machine (using a recovery DVD) is that depending on the options available to you, the Ubuntu partition might not have to be wiped - look for an option which says something about "do not repartition"

---

### Post by pastalavista on 2009-04-08
> **mb_webguy said:**
> +1

Recovery partitions restore the computer to its original state, so unless that original state included an Ubuntu installation, The Ubuntu partition will be overwritten.

IF, however, the System Recovery partition is lost or damaged, AND you have a Windows install disk, it will install only in the allocated NTFS
space. It won't see the ext3 partition at all.

---

### Post by mb_webguy on 2009-04-08
> **pastalavista said:**
> IF, however, the System Recovery partition is lost or damaged, AND you have a Windows install disk, it will install only in the allocated NTFS
space. It won't see the ext3 partition at all.

Ah, but that's not restoring the system from a recovery partition, is it?  ;)

---

### Post by anaconda on 2009-04-08
With my HP laptop, Recovery from the recovery partition didn't erase ubuntu. (I expexted it would erase everything.) It did overwrite grup though.

The recovery just installed windows to the first partition.

I think this will vary between different manufacturers. So good luck.

---

### Post by mb_webguy on 2009-04-08
> **anaconda said:**
> With my HP laptop, Recovery from the recovery partition didn't erase ubuntu. (I expexted it would erase everything.) It did overwrite grup though.

The recovery just installed windows to the first partition.

I think this will vary between different manufacturers. So good luck.

Wow... what a polite recovery partition.  The few times I've tried to use a Dell or Gateway recovery partition, it repartitioned the drive on which the recovery partition resided so that only the recovery partition and the Windows partition was left.

---

### Post by nimonika on 2009-04-08
OK, doing the job now,so will post later what really happened with recovery on vaio....

---

### Post by nimonika on 2009-04-08
After running the XP recovery partition,

1. Windows XP was installed successfully
2. I did not loose the grub boot menu loader (gulp!!)
3. My ubuntu partition is intact (posting this from there)

I almost fainted with shock.....

---

### Post by maheshasolkar on 2009-04-08
> **nimonika said:**
> After running the XP recovery partition,

1. Windows XP was installed successfully
2. I did not loose the grub boot menu loader (gulp!!)
3. My ubuntu partition is intact (posting this from there)

I almost fainted with shock.....

That is certainly nice to know. I have, time and again, postponed the plan to refresh XP on a vaio notebook thinking I'd have to redo Ubuntu installation again. Now I can try my recovery partition out!

---

### Post by anaconda on 2009-04-09
> **nimonika said:**
> 
2. I did not loose the grub boot menu loader (gulp!!)
I almost fainted with shock.....

You DIDN't lose grub? THAT is surprising. I would even say that it is not good. 

Windows recovery should always end with a working and booting machine. And so if you have a borked ubuntu install with a nonworking grub on your hard-disk, then the recovery won't install a working system for you..

Yup.. Myself I would also like to have windows install itself without breaking grub, but just thinking about  a windows user that tries ubuntu and wants to go back....

---

