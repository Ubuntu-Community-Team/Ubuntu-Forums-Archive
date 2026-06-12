---
title: "GRUB dual boot problem"
date: 2005-12-13
forum: General Help
---

### Post by Swoop on 2005-12-13
Hi
I have been running ubuntu on my laptop for quite some time now and im extremely happy with it.
So i decided why not get some experience with ATI drivers ect on a larger machine like my desktop machine. But since i want to keep my games ect working i need a dual boot on that one. I tried installing breezy and having it use the free 25 GB space i left (80 GB drive with some 25 gigs free and unpartitioned). Installer goes fine, and asks me if i want to install grub to MBR.
I do of course (dont i ?) and when the install is finished it boots perfectly to ubuntu if i dont choose anything else in grub.

BUT if i choose to boot windows xp professional i get this error shortly, and then the computer restarts to put me back in the grub menu again:

```

root (hd0,0)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1


```


Now i dont have a clue as to how to fix this, and searching havent provided me with much informatation im afraid :(
Wierd thing is that i could boot just after the first boot without problems, but now i cant seem to get it working :(

Any suggestiong woud be greatly appriciated so i can start working on my better machine :D

---

### Post by dubz on 2005-12-13
instead of using root...use the rootnoverify command in grub

that should sort out your problem

---

### Post by Swoop on 2005-12-13
Thanks a million !
Works like a charm, so now i can move on to getting this setup runnin smooth and creamy :D 

Thanks again ! :D :D

---

### Post by Swoop on 2005-12-16
Well im afraid i have problems still.
XP boot wont work untill i have booted Linux first, and then even at random times it will reboot instead of booting xp.

Im sooooo lost for what to do :(

---

### Post by livingtarget on 2005-12-16
Ok this is a bit advanced but I use wingrub, in other words I got the default windows bootloader in which i can choose to launch wingrub which will launch linux for me. It's not faultless but it is the best solution I found, it leaves my windows XP on my primary harddisk well alone.

Disclaimer: This is tricky to get to work, if you got grub already installed then you'd need to restore the windows MBR and install grub to the first sector of the partition you are installing it in. Note: there should be an option during your install to install grub like this.

---

### Post by Swoop on 2005-12-16
hmmm sounds a bit tricky :(
Dont see why this shouldnt work.. both windows and linux is on the same primary harddrive. Have had dual boots before working without a problem.

Hope i can find some way to make grub boot correctly... next time im gonna see if there is an error before the reboot when i choose winxp ... gotta be a solution :D

Suggestions welcome ;) rootnoverify didnt work completely :(

---

