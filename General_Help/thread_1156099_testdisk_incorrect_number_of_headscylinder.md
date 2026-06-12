---
title: "testdisk: incorrect number of heads/cylinder"
date: 2009-05-11
forum: General Help
---

### Post by zorkerz on 2009-05-11
I'm having some problems with my partition tables detailed [here]("http://ubuntuforums.org/showthread.php?p=7257947#post7257947"). TestDisk is giving me the following warning
```
Warning: incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
```I don't really know what this means does anyone else? 
I have tried changing the disk geometry to 240 and 16 but neither provide as accurate of a partition layout as 255 which it is set at.

SIDE-NOTE: I put the warning in CODE tags is better to put it in QUOTE tags? I've had people give me crap for putting things in the wrong tags before but this case seems ambiguous to me. Its would not be code because you never need to type it and its sorta a quote because testdisk "said" it.

thanks

---

### Post by matey3 on 2009-05-11
In the old days when the motherboards could not handle more than 4 GB hard drives we had to change the number of cylinders and lower them and then add to the number of heads bcs the size of partition reported to the OS is number of cyl x number of heads so since it was a multiple sum of the 2 numbers it didnt matter and it worked 
most old BIOS had a limit on number of cylinders but not the heads, 
I dont think you had that problem so may be the setting in your bios was wrong to begin with?
if you change the numbers tho you will get a lot of garbage instead of data.
meaning whatever the bios was set at you have to fdisk and format that way.
cannot change the cylinder and heads later.

---

### Post by zorkerz on 2009-05-11
I don't know if this helps but I should have mentioned this before. I am pretty sure this occured because I installed TinyXP. Meaning the XP install appears to have screwed with the number of heads/cylinder.

---

