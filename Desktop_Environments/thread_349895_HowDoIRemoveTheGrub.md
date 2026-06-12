---
title: "HowDoIRemoveTheGrub?"
date: 2007-01-30
forum: Desktop Environments
---

### Post by rabidsnakemonkey on 2007-01-30
so, despite some problems in the beginning, ubuntu worked well for me. Eventually, i stoped using it, however, because i had Windows XP as a diferent partition on another harddrive. well one day i wanted to see how ubuntu was doing, so i tried to boot it. well, it stopped mid-way through with an error twice, and i didnt want to bother with figuring out what the problem was.

I booted windows and used the disk manager to remove the partition of the ubuntu disk. then i created a new windows partition on it as a backup hard drive (the 20gigs of extra space didnt hurt, with all the music i have on my computer). Anyway, when is tried to start it again, the grub was still on the computer, trying to load what didnt exist. i tried playing with my bios settings, but that didnt work. i even took the watch battery thing out of my motherboard, hoping that would reset some stuff (besides, i dont mind resetting the clock).

I still have a problem. if there is a way to remove the grub, that would be helpful. i might just re-install ubuntu, and then remove it from inside ubuntu if i dont want it.
Any suggestions would be great. thanks!

(btw: this is an awsome smilie: :guitar: )

---

### Post by mister_p_1998 on 2007-01-31
Easy!

open a command prompt and type
fdisk /mbr


Steve

---

