---
title: "HELP!! Dual boot gone wrong.. Partition problem"
date: 2009-04-30
forum: General Help
---

### Post by leegro on 2009-04-30
Hey, I set up a 25 gb ntfs partition prior to installing ubuntu.  When installing i did the automatic thing and I guess it made its own partition?  So it made the partition to only be like 2.5 gbs.  And now that is full, but I have this 25 gb partition just laying around. How can I merge the two?  I am trying with gparted on the 9.04 live cd but dont know what I am doing.

---

### Post by codeseer on 2009-04-30
Provided you don't care about the data on the 25 GB partition, assuming it's blank, you can delete it and then resize the Ubuntu partition to consume that new free space by booting into the live CD and using GParted.

---

### Post by leegro on 2009-04-30
it is not allowing me to do that 
this is what it looks like
/dev/sda1 recovery 14.75 gib
/dev/sda2 windows partition 256 gib, 167 unused
/dev/sda4 (has some key icon next to it) 2.50 gib 2.22 used

now I can expand /sda4 and it has /sda5 in ext3 file system and /sda6 with keys next to it in linux - swap

finally i have 25 gibs of unuallocated.  
what can i do?

---

### Post by leegro on 2009-04-30
here is a screenshot of it

---

### Post by codeseer on 2009-04-30
> **leegro said:**
> here is a screenshot of it

I see. You have that all in one extended partition. You will need to resize the 'extended' one, the light blue. then move the swap to the end of the extended and then resize the root.

---

### Post by leegro on 2009-04-30
i cant the swap is locked and I cant do anything with it.. I thnk I need to make a seperate gparted cd.

---

### Post by codeseer on 2009-04-30
> **leegro said:**
> i cant the swap is locked and I cant do anything with it.. I thnk I need to make a seperate gparted cd.

Is it mounted?

---

### Post by leegro on 2009-04-30
i read that the swap is what you are using when u are booting from the live cd that is why it cant be unmounted or anything

---

### Post by codeseer on 2009-04-30
> **leegro said:**
> i read that the swap is what you are using when u are booting from the live cd that is why it cant be unmounted or anything

Well that's odd. I can see a need for it on lower end machines, but obviously it limits people. You could try a gparted live cd instead of an ubuntu cd.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by caljohnsmith on 2009-04-30
You can "unmount" the swap partition simply by right-clicking it in gparted, and select "swapoff". Then you should be able to make your partition changes. Let us know how it goes. :)

Cheers,
John

---

