---
title: "KDE and memory stick :("
date: 2006-02-17
forum: Desktop Environments
---

### Post by natman on 2006-02-17
Hi i had GNOME working fine and when i plugged in my external memory stick ( one of those flash drive's) it poped up on the desktop.
I just got KDE and when i plug in the memory stick, nothing happens, how can i acces it?
Anyone help?
Thanks:

---

### Post by Denta on 2006-02-17
Hello, I'm using a swedish version of KDE so I don't know the exact names of the menus - but here's a try;

K-menu -> System settings ->Disk & Filesystems -> Adminsitrator mode

Look up your device, mark it and press New.

---

### Post by natman on 2006-02-18
Thanks, will try that, also have found out that if ou click konqorour and look in removable media its already there.
Thanks:

---

### Post by der_joachim on 2006-02-18
[QUOTE=natman]Thanks, will try that, also have found out that if ou click konqorour and look in removable media its already there.
Thanks:[/QUOTE]

Have you run all updates? The vanilla version of Kubuntu 5.10 had a slightly buggy KDE version which did no automounting. 

Furthermore, I have seen that KDE refuses to automount a memory stick with a FAT16 FS (which some still have for some dumb reason). I've not found a solution for that yet (OTOH, I never seacrhed. ;)).

---

### Post by katiad on 2006-02-20
I had this problem, but doing:

> pmount /dev/sdb1

And then checking /media for a new folder named sdb1 worked. :) Apparently these things usually mount on sdb1 or sdb2 or so. 

Typing the following in the terminal may give you an idea of whether your usb drive was recognized. (At the end, there were a bunch of lines indicating that yes indeed, my usb drive was recognized automatically.)

> dmesg

I, uh, haven't figured out how to make this happen automatically yet. But doing it from the terminal manually will do for now for me, at least. Perhaps someone here will lend a hand...

---

