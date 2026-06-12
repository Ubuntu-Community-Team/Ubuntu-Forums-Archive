---
title: "Problem with Warcraft"
date: 2007-03-13
forum: Gaming &amp; Leisure
---

### Post by nick_533 on 2007-03-13
Hi I reformatted windows and installed ubuntu only


now i have complete wow setup (installed in other partition) 

now with wine can i give link to Launcher.exe file and run wow ?

thanks

i just dont want to copy wow+bc lo my HD and intall all over again 
:mad:

---

### Post by Moeru on 2007-03-13
> **nick_533 said:**
> Hi I reformatted windows and installed ubuntu only


now i have complete wow setup (installed in other partition) 

now with wine can i give link to Launcher.exe file and run wow ?

thanks

i just dont want to copy wow+bc lo my HD and intall all over again 
:mad:

If WoW is installed on a FAT32 partition, you should have no problem navigating to it. If it is on a NTFS partition, clicking on Places and then Network Shares should show you the hidden XP shares (C$,etc). You can get to it there to copy or share it on your XP side and then copy it from there.

Once in, you'll be copying it to home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/  (This is the default directory on both Operating Systems)

---

### Post by nick_533 on 2007-03-13
lol both ways again i got to copy all 8 gb

---

### Post by Ferrat on 2007-03-14
> **nick_533 said:**
> lol both ways again i got to copy all 8 gb

Yes, there is no good way getting around that but if you got SATA disks it should take like a few minutes

---

