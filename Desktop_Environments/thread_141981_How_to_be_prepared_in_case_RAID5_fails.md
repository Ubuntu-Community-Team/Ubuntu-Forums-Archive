---
title: "How to be prepared in case RAID5 fails?"
date: 2006-03-09
forum: Desktop Environments
---

### Post by edopizza on 2006-03-09
Hello! 
I eperienced a boot faliure on my pc set up with RAID5 (8 data plus 1 spare disk). With knoppix I was able to mount and access the boot driver. The physical RAID5 disks were also detected but it was impossible to see the data stored on theirs software disks. 
I then reinstalled all the system. 
Is there a way to prevent future prolems by having the files that control and reconstruct the software disk backed up somewhere? If yes, what is the procedure to access the data?  (be aware, I am a new-newbee...)

---

### Post by dcstar on 2006-03-10
[QUOTE=edopizza]Hello! 
I eperienced a boot faliure on my pc set up with RAID5 (8 data plus 1 spare disk). With knoppix I was able to mount and access the boot driver. The physical RAID5 disks were also detected but it was impossible to see the data stored on theirs software disks. 
I then reinstalled all the system. 
Is there a way to prevent future prolems by having the files that control and reconstruct the software disk backed up somewhere? If yes, what is the procedure to access the data?  (be aware, I am a new-newbee...)[/QUOTE]
Simple, set one disk as a stand-alone boot/system disk and use the rest in the RAID array.

If anything goes amiss with the first disk, it can be rebuilt without affecting the RAID array.

---

### Post by edopizza on 2006-03-10
>Simple, set one disk as a stand-alone boot/system disk and use the rest in the >RAID array.

>If anything goes amiss with the first disk, it can be rebuilt without affecting the RAID >array. 

Right, but will the guided install procedure of ubuntu be able to detect the old RAID5 sofware disk and ribuilt it?

---

### Post by dcstar on 2006-03-10
[QUOTE=edopizza]>Simple, set one disk as a stand-alone boot/system disk and use the rest in the >RAID array.

>If anything goes amiss with the first disk, it can be rebuilt without affecting the RAID >array. 

Right, but will the guided install procedure of ubuntu be able to detect the old RAID5 sofware disk and ribuilt it?[/QUOTE]
I'm not sure, but if you don't format/repartition the drives and set them up in the same RAID structure as before, there shouldn't be any reason for them to be changed.

Easiest thing to do would be to try it and see if it goes - since you have just rebuilt your system you may not have much to lose (except a bit of time).

---

