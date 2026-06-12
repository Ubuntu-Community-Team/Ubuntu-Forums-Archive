---
title: "RAM not being shown right"
date: 2009-03-30
forum: General Help
---

### Post by Nitewalker on 2009-03-30
I have just updated my RAM to 4gb but it is not being shown, what do I need to do, it is installed on an Acer Aspire 5100 with a AMD 64x2 processor?  this is what I get when I run "free -m" and "free":confused:

nitewalker@smj:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2276        610       1666          0         50        236
-/+ buffers/cache:        322       1953
Swap:         1757          0       1757
nitewalker@smj:~$ free
             total       used       free     shared    buffers     cached
Mem:       2331276     689492    1641784          0      54228     290844
-/+ buffers/cache:     344420    1986856
Swap:      1799240          0    1799240
nitewalker@smj:~$

---

### Post by aeiah on 2009-03-30
are you using the 64bit version of ubuntu? the 32bit version cant see all 4GB

---

### Post by aeiah on 2009-03-30
you might also want to check your bios. i could be going mad but i think some motherboards are a bit weird and have a setting to limit ram to protect windows xp 32bit from getting confused.

---

### Post by hyper_ch on 2009-03-30
when posting output use [noparse]```

```[/noparse] brackets around it to make it easier to read.

---

### Post by Nitewalker on 2009-03-30
I am using the 32 bit version of Ubuntu 8.10 disc as I was not sure if my laptop was 32 or 64 bit?  Is there anyway I can find out from the terminal:confused:

I orginaly installed Ubuntu 8.10 from disc and then upgraded to KDE which now shows I have "Kubuntu".  Is this creating any problem and should I uninstall the OS and reinstall Ubuntu 8.10 using 64bit disc, and not upgrade to KDE:confused:

Bios does show RAM to be just under 4gb.  I have a dual boot with XP but the XP will only show 2gb installed even though Bios shows almost 4gb

Will in future put brackets around terminal outputs as requested for clairifcation sake, sorry I did not know I should do that.

---

### Post by MysticGold04 on 2009-03-30
Thats interesting because 3GB is the limit that is accessible to 32 bit OSes.  Your XP should read 3GB of Ram.  What does the Ubuntu installation say?

---

### Post by DeMus on 2009-03-30
> **MysticGold04 said:**
> Thats interesting because 3GB is the limit that is accessible to 32 bit OSes.  Your XP should read 3GB of Ram.  What does the Ubuntu installation say?

Well, actually 32-bits systems can address 2^32=4294967296 bytes. This large numbers equals 4GB.
The problem is the OS's use some of the 4GB themselves, leaving less for the user. What's left is around 3GB.
Why 64-bits don't suffer this is strange. Okay, they can address much more memory ( 2^64=18446744073709551616 bytes ). But when you have 4GB installed, why the OS doesn't take some of it now? Why now the full 4GB is available to the user? Anyone?

---

### Post by Nitewalker on 2009-03-31
Thanks for all the help, I deleted the 32bit OS and reinstalled Ubuntu 8.10 64bit OS, now when I check for ammount of RAM it is showing the 4 gb.

---

