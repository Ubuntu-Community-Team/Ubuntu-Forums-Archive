---
title: "unusual conflict with at startup"
date: 2008-12-17
forum: General Help
---

### Post by lordbalmung on 2008-12-17
[COLOR="SeaGreen"]Drive d (d: ) used to be my default windows drive, I formatted c: and installed ubuntu, no problem in that, however[/COLOR]

[COLOR="Red"]Problem: Cannot access XP, probably because all the boot files required were in c: and were deleted...[/COLOR]

Rectifications tried: **tried editing the menu.lst**, however, it proved to be useless, **perhaps i did not edit it properly.**

In any case, is there a way to (re)use xp without reinstalling windows all over again...?

*So basically, the unusual startup conflict was caused by me, so i need your help to solve it* :confused:

---

### Post by Izek on 2008-12-17
Just so you know, Ubuntu doesn't see drives as letters. ubuntu sees them as media/disk for removables and I believe sda/hda for harddrives and media/cdrom for cd/dvds.

Now, for your windows problem. Once you do get back into windows, you need to change the drive [letter manually (click here)]("http://www.petri.co.il/change_system_drive_letter_in_windows_xp.htm").

If you want to edit the registry from linux...

[Google Search](http://www.google.com/search?hl=en&lr=&ie=UTF-8&safe=off&q=linux+%22windows+registry%22&btnG=Search)

OR if you can access the site: [http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

---

### Post by sedawk on 2008-12-17
If installation worked fine your grub menu should offer you a number
of different boot systems:
1) ubuntu and ubuntu recovery

1.1) ubuntu and ubuntu recovery for older kernels (optional, most likely
after upgrading and newer kernels were available)

2) windows

Do you have that "windows" entry and what happens if
you try to boot using that menu entry?

btw: you do not have to reinstall windows, you can use
  a windows CD (recovery console) to repair the boot system of windows.
  But that will overwrite grub, so you reinstall grub and are back at
  start.

---

### Post by lordbalmung on 2008-12-18
> **sedawk said:**
> If installation worked fine your grub menu should offer you a number
of different boot systems:
1) ubuntu and ubuntu recovery

1.1) ubuntu and ubuntu recovery for older kernels (optional, most likely
after upgrading and newer kernels were available)

2) windows

Do you have that "windows" entry and what happens if
you try to boot using that menu entry?

btw: you do not have to reinstall windows, you can use
  a windows CD (recovery console) to repair the boot system of windows.
  But that will overwrite grub, so you reinstall grub and are back at
  start.

oh ho, so in short i'll have to reinstall ubuntu, am I correct?

let me summarize:

1. use windows recovery (through installation cd)
2. [forget ubuntu], change D: to C:
3. reinstall ubuntu in the old ext3 drive
4. feel very happy and proud to have used ubuntu forums..

did i get them right?

---

### Post by lordbalmung on 2008-12-18
> **Izek said:**
> Just so you know, Ubuntu doesn't see drives as letters. ubuntu sees them as media/disk for removables and I believe sda/hda for harddrives and media/cdrom for cd/dvds.

Now, for your windows problem. Once you do get back into windows, you need to change the drive [letter manually (click here)]("http://www.petri.co.il/change_system_drive_letter_in_windows_xp.htm").

If you want to edit the registry from linux...

[Google Search](http://www.google.com/search?hl=en&lr=&ie=UTF-8&safe=off&q=linux+%22windows+registry%22&btnG=Search)

OR if you can access the site: [http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

err... from what i understand, changing the registry would solve the problem, and it can be done through ubuntu, is that it?, then what should i change in the registry to change the drive letter?

---

