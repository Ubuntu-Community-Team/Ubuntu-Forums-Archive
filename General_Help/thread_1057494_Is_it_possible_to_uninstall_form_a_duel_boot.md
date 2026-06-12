---
title: "Is it possible to uninstall form a duel boot?"
date: 2009-02-01
forum: General Help
---

### Post by Jynks on 2009-02-01
As I understand it.. the duel boot in grubb is just a file on the hdrive and it is "virtual" partitioning...

Is there a way I can remove this and ubuntu and get my file space back on my vista partition? Basically uninstalling ubuntu and removing the duel boot?

Thanks in advance

---

### Post by hardyn on 2009-02-01
did you use wubi to install?  or straight up vanilla install?

ps.

duel is something you do with swords.
dual is two of something.

---

### Post by x33a on 2009-02-01
if you want to remove ubuntu, you'll have to delete its partition, and make changes/fix the bootloader.

---

### Post by Jynks on 2009-02-02
> **hardyn said:**
> did you use wubi to install?  or straight up vanilla install?

ps.

duel is something you do with swords.
dual is two of something.

I used the visual install that came on teh iso that i downloaded.

---

### Post by Jynks on 2009-02-02
Any ideas?

---

### Post by hajbal92 on 2009-02-02
For me the solution was: 

I have done this 3 times ago before decding to use Win or Ubuntu, and it  works fine.

Step 1: Start the windows.
Step 2: Download a boot manager, Boot-us is free [http://google.com](http://google.com) it
Step 3: right click in the start menu on My Computer and choose manage
Step 4: find the Partitions and simply delete the UBUNTU partition + Swap
Step 5: MAKE SURE AND INSTALL THE BOOT MANAGER -- If you miss this step you have ruined your computer, you will loose all of your data, because you cannot start your windows...
Step 6: After install set windows the main OS and reboot your PC.


ps. I wouldnt uninstall ubuntu ... I would uninstall WINDOWS

---

### Post by hajbal92 on 2009-02-02
> **hardyn said:**
> 
duel is something you do with swords.
dual is two of something.

OMG ROFL LOL:lolflag:

---

### Post by hardyn on 2009-02-03
or boot your windows CD. enter recovery console

"fixmbr"

reboot

and use disk manager to delete the ubuntu partition.

---

### Post by JohnWesleyMethodist on 2009-02-03
> **hardyn said:**
> 
duel is something you do with swords.
dual is two of something.

 Apparently Windows and Ubuntu had a duel and Ubuntu has lost...

---

### Post by alwarnecke on 2009-02-05
how would i delete using disk manager? i see that it says delete volume, so would that just merge it with my other primary volume?

---

### Post by hardyn on 2009-02-06
or run as an addionial partition.

---

