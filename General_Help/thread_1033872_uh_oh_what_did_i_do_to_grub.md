---
title: "uh oh what did i do to grub"
date: 2009-01-07
forum: General Help
---

### Post by sPiN1 on 2009-01-07
I had Ubuntu installed just fine, installed windows xp on another partition for gaming purposes... Went onto my live disc and installed grub again because windows wiped it out, now I can't get on windows or ubuntu, I get Error 17: cannot mount volume (or something like that) on ubuntu)) and Error 13 (i think) recieved another weird error for windows)) can anybody help me get my computer back into order so I can continue to game and use ubuntu? It doesn't seem like a hard thing to fix I just don't want to mess with something and ruin it.

---

### Post by adult swim on 2009-01-07
paste the output of ```
sudo fdisk -l

cat /boot/grub/menu.lst
``` here

---

### Post by sPiN1 on 2009-01-07
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16363   131435766    7  HPFS/NTFS
/dev/sda2   *       16364       29537   105820155   83  Linux
/dev/sda3           29538       30017     3855600   83  Linux
/dev/sda4           30018       30394     3028252+   f  W95 Ext'd (LBA)
/dev/sda5           30018       30394     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

### Post by adult swim on 2009-01-07
the easiest way to fix it would be to install grub from a live cd again like you tried earlier but use these commands from a terminal
```
sudo grub

root (hd0,1)

setup (hd0)

exit
``` then restart your computer and boot into ubuntu.  you probably wont have the option to boot into windows yet but we can fix that.  once ubuntu is up and running go to a terminal and run ```
gksudo gedit /boot/grub/menu.lst
``` and then go to the very bottom of the file and paste in ```
title		Windows
root		(hd0,0)
chainloader	+1
``` then save and close the file and you should be good to go.

---

### Post by sPiN1 on 2009-01-07
grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 

I get that error still, the one that won't let me boot to it as well.

---

### Post by adult swim on 2009-01-07
i edited my first post i made  a mistake.  try root (hd0,1) and then setup (hd0)

---

### Post by sPiN1 on 2009-01-07
ok that got one linux partition to work but not the other, and the other is the one i used most, do you know how i can get the other to work rather than this one? i don't even know why i have two ubuntu's lol

edit: i'd like the 100gb one to work.

---

### Post by adult swim on 2009-01-07
:)  i was wondering what that second linux partition could be.  to do that from live cd use ```
sudo grub

root (hd0,2)

setup (hd0)
```

---

### Post by sPiN1 on 2009-01-07
ok I did that, I was wondering I have a few more questions that can be more easily answered over AIM or MSN if you can help me over that please let me know your email via pm and i would greatly appreciate it!

---

### Post by sPiN1 on 2009-01-07
Alright I did it with 0,2 and rebooted and got the errors I had before where i cannot boot from an operating system.

---

### Post by sPiN1 on 2009-01-07
can somebody help me with this? I'm stuck using the live disc right now! :(

---

### Post by sPiN1 on 2009-01-07
ok i'm installing linux on the little 3gb partition i have for a fresh version of grub hopefully it'll get everything working correctly wish me luck!

---

