---
title: "Enlage Ubuntu Shrink XP"
date: 2009-03-20
forum: General Help
---

### Post by joelwhrs on 2009-03-20
I have been trying to enlarge the ubuntu partition but when i use the live cd to boot and then go into the partition editor and try to shrink the windows partition it just says that it cant read the files or something like that. Any help would be greatly appreciated.

---

### Post by hikaricore on 2009-03-20
A more accurate error than "can't read the files or something like that" might be helpful.
Please try it again from the live cd and write down any errors you get.

You may have to install additional packages if the partition is ntfs, I've not delt with it myself but I did see a thread quite recently about it in general help.

---

### Post by joelwhrs on 2009-03-21
It is ntfs if that helps any but if i click on it it just says that it cant read the files.

---

### Post by Rallg on 2009-03-21
Although I cannot answer your question, while you are waiting, try this: In Windows, do a file system check, then de-fragment the Windows drive. Later, that will make the partition editor run faster when you solve the problem about shrking the XP partition.

---

### Post by joelwhrs on 2009-03-21
I have already run the file system check and it cant complete it, it just says that the check can't be completed:((

---

### Post by lunatico on 2009-03-21
You won't be able to do this from the live CD.
Get a [GParted]("http://gparted.sourceforge.net/index.php") Live CD and boot from it.

The way to do this is a bit tricky, but it works. I did it like a month ago so let's see if I can remember all steps:

1. Boot into GParted
2. Shrink your XP partition. I suppose you have two physical partitions and one logical partition inside of each. So the first time you shrink your windows partition you are only doing it on the logical one, so after that you need to shrink the physical one to leave unallocated space.
3. Then you need to move your Linux physical partition to fill that unallocated space and then you fill all that with the logical partition.

Or something among those lines...

Remember always to back up when doing this things. I never do it myself, but I recommend it....

---

### Post by joelwhrs on 2009-03-24
Hey I got it figured out, I just needed to run the chkdsk /f in windows and everything worked great, but thanks anyways.

---

### Post by lunatico on 2009-03-25
> **joelwhrs said:**
> Hey I got it figured out, I just needed to run the chkdsk /f in windows and everything worked great, but thanks anyways.

Excellent! So how did you resized the partitions at the end?

---

### Post by joelwhrs on 2009-03-25
I just used gparted live cd and resized everything I wanted to, it worked great!!!

---

