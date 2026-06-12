---
title: "Dual booting Error"
date: 2005-12-10
forum: General Help
---

### Post by JoshHendo on 2005-12-10
I am having trouble trying to get GRUB working.
I posted in a thread I started, [http://ubuntuforums.org/showthread.php?t=101487](http://ubuntuforums.org/showthread.php?t=101487) , though it was getting off topic, so I am starting a new thread :).
I get error 20, and I am told by the grub website that it means:
20 : Multiboot kernel must be loaded before modules
This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of such modules to a non-Multiboot-aware kernel. 
Does anyone know how I can fix this problem, or install another thing like LILO (I can't work out how to easily install that :P). Thanks :)

---

### Post by JoshHendo on 2005-12-10
woops :P.
it is error 25 not error 20.  Accordiong to the GRUB site that means....
25 : Disk read error
This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 
Is there any way that I can get more info so I know what disk it can't read off? I am assuming it is the HDD setup as the HDD I installed ubuntu on is a slave. My first aim was to do this with the partitioning.
hda1 (master)
#1 | windows
#2 | partition for one user of the computer
#3 | partition for another user of the computer etc.... (there are 5 users in total)

hda2 (slave)
#1 | ubuntu
#2 | swap
#3 | share (a partition that both windows and linux can read)


I am assuming I would have to do something like this to fix the error. It would be great if someone could tell me if this **should** work :) :

hda1 (master)
#1 | windows
#2 | ubuntu
#3 | swap

hda2 (slave)
#1 | share
#2 | partition for one user of the computer
#3 | partition for another user of the computer etc....

---

