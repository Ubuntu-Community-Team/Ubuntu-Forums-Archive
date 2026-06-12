---
title: "Deleting Ubuntu."
date: 2009-05-14
forum: General Help
---

### Post by Taz. on 2009-05-14
Hey ubuntu pros :D

Well, I installed ubuntu on a machine. Without any dual-boot.. I wanna remove it.. So i put my windows cd, but it doesnt boot it.. Can I sumhow, delete ubuntu ?

thanks guys :)

---

### Post by adamspurgin on 2009-05-14
> **Taz. said:**
> Hey ubuntu pros :D

Well, I installed ubuntu on a machine. Without any dual-boot.. I wanna remove it.. So i put my windows cd, but it doesnt boot it.. Can I sumhow, delete ubuntu ?

thanks guys :)

well, you could put a program like "gparted" on a live-cd and boot off of the disk, it's a partition manager that will allow you to make your entire disk "unnalocated" among other things

---

### Post by Taz. on 2009-05-14
Can I just delete the section where ubuntu is ? And then install xp from boot ?

---

### Post by connorh123 on 2009-05-14
> **Taz. said:**
> Hey ubuntu pros :D

Well, I installed ubuntu on a machine. Without any dual-boot.. I wanna remove it.. So i put my windows cd, but it doesnt boot it.. Can I sumhow, delete ubuntu ?

thanks guys :)
Do you mind me asking why you don't like it. And why you even tried it?

---

### Post by Carl Hamlin on 2009-05-14
> **Taz. said:**
> Hey ubuntu pros :D

Well, I installed ubuntu on a machine. Without any dual-boot.. I wanna remove it.. So i put my windows cd, but it doesnt boot it.. Can I sumhow, delete ubuntu ?

thanks guys :)

Will the machine boot other CDs? The presence of Ubuntu on your machine is unlikely to be the cause of the inability to boot from the CD-ROM. If you can't boot other CD-ROMs, I'd start looking in the BIOS and make sure the boot settings are setup the way you want them.

---

### Post by Taz. on 2009-05-14
Ofc i can tell you :) I LOVE ubuntu. I had this old machine, i wanted to test the speed.. with ubuntu. Its faster.. But i use ubuntu on my main PC (laptop), i have vista and ubuntu on my laptop. Thats what i mainly. Do you have an idea how to delete it ?

---

### Post by adamspurgin on 2009-05-14
> **Taz. said:**
> Can I just delete the section where ubuntu is ? And then install xp from boot ?

yup, it works just like the disk manager in XP/Vista, only better. it's faster, more efficient, and it won't give you confusing error messages.

now, do you already have xp on a partition?

---

### Post by Taz. on 2009-05-14
As I already said, all I have is ubuntu.. Its installed on the WHOLE HDD..

---

### Post by adamspurgin on 2009-05-14
yeah, so "gparted" will do the trick just fine

---

### Post by Taz. on 2009-05-14
Ty, ill give it a try. And get back to you.

---

### Post by Taz. on 2009-05-14
Ok guys, i have a problem... It does not let me boot from the live-cd.. Before i installed ubuntu, i could boot from cd, not anymore.. any idea ?

---

### Post by BslBryan on 2009-05-14
Hello, Taz. :-)

Well, you need to edit your BIOS settings to boot from CD-Rom, it looks like.

Let me know if that does the trick.

---

### Post by Taz. on 2009-05-14
I already did. My dvd drive is number one. Still not working.

---

### Post by BslBryan on 2009-05-14
Hmm...   What happens after you put the LiveCD in?

---

### Post by Taz. on 2009-05-14
My pc, loads normaly. Then it asks, if i wanna continue to the grub menu or normal boot..

---

### Post by BslBryan on 2009-05-14
What are the options on the GRUB menu?

---

### Post by MontelEdwards on 2009-05-14
I guess there is no way to "delete" ubuntu as it is sofware or something. You are booting the CD from your BIOS right? Are you sure that your BIOS is configured correctly? That is the problem for most of the  people.

---

### Post by BslBryan on 2009-05-14
Deleting Ubuntu is definitely possible.  Deleting anything on any drive is possible.  ;-)

Anyway, he's confirmed that his BIOS is configured correctly.

---

### Post by Taz. on 2009-05-14
Ill check the BIOS again.

I have:

The normal boot
The normal but a "recovery"
normal boot but another version (lower one)
normal boot but a lower version recovery
memtest

---

### Post by BslBryan on 2009-05-14
Make sure that if, first, there is no DVD present, you can boot from CD.

---

### Post by Taz. on 2009-05-14
I GOT SUMTHING ! When I boot it says, Primary slave drive fails... and my primary slave is my dvd drive. My primary master is my HDD.. What may i do ?

Edit: Im trying to play with the options .. But still nuuthing..

---

### Post by MontelEdwards on 2009-05-14
Well thats what i meant.
There is no uninstall app or something.
The only way is to format the partition or delete it from the drive

---

### Post by Taz. on 2009-05-14
I got the problem. We need the solution. It says my drive is failing. But the drive works on another PC.. I put the drive as primary slave or other it still doesnt work.

---

### Post by Taz. on 2009-05-14
Managed to get it to work.. This can be closed. THANKS ALOT GUYS :)

---

