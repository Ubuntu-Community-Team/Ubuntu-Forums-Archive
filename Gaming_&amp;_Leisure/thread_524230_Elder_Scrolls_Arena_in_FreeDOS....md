---
title: "Elder Scrolls: Arena in FreeDOS..."
date: 2007-08-12
forum: Gaming &amp; Leisure
---

### Post by the_darkside_986 on 2007-08-12
Has anyone gotten the freeware version of Elder Scrolls Arena to work in FreeDOS? I had to run the executable in Wine first, and then copy the unzipped files to the FreeDOS system, but when I try to run it, it simple freezes with a blank screen. I'm not familiar with *DOS but I have gotten other old games like simcity2k, tes2:daggerfall, and themepark working.

---

### Post by dmn_clown on 2007-08-12
> **the_darkside_986 said:**
> Has anyone gotten the freeware version of Elder Scrolls Arena to work in FreeDOS? I had to run the executable in Wine first, and then copy the unzipped files to the FreeDOS system, but when I try to run it, it simple freezes with a blank screen. I'm not familiar with *DOS but I have gotten other old games like simcity2k, tes2:daggerfall, and themepark working.

It runs almost perfectly in dosbox without the need for wine.

---

### Post by the_darkside_986 on 2007-08-12
Well, I have it working in dosbox, but I would like to have it working on the old PC running FreeDOS in the other room so that the guest(s) who stay could also play. It is an old system too old to run Ubuntu and dosbox. My nephew enjoys playing Daggerfall on that machine when he is here.

I think the problem may be a faulty cd-rw disk. CD and floppy are the only drives that will work in FreeDOS because my USB thumb drive isn't recognized. It is a compaq presario made before or in '98 so that explains why the DOS cannot use the BIOS to access USB :(. I don't think there is a way to upgrade the BIOS either...

---

### Post by the_darkside_986 on 2007-08-13
BTW, does anyone know what the grub entry for FreeDOS is? I would like to dual-boot it with other OS like Linux or something but I can't find any information about FreeDOS, even the correct grub entry. I guess there is a particular kernel file in FreeDOS that should appear on the menu.lst but I can't even find which one it is.

---

### Post by dmn_clown on 2007-08-13
Have you tried it with any other GNU/Linux Distribution?  Slackware and Debian are very good with older hardware as is DSL and Puppy (though Puppy is non-free).

---

### Post by Frem on 2007-08-14
> **the_darkside_986 said:**
> BTW, does anyone know what the grub entry for FreeDOS is? I would like to dual-boot it with other OS like Linux or something but I can't find any information about FreeDOS, even the correct grub entry. I guess there is a particular kernel file in FreeDOS that should appear on the menu.lst but I can't even find which one it is.

You should be able to use the same grub entry you would use for Windows. Just point it to the correct partition (The "root(hd0,0)" part).

Example:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

In answer to your question about the DOS kernel, DOS and FreeDOS both boot off "COMMAND.COM", which should be in "C:\". However, you don't need to give GRUB that information.

Also, you may need to have FreeDOS on the first partition. I'm not sure if it's as picky as Windows 98 is about that.

---

### Post by the_darkside_986 on 2007-08-14
I'll try that then. thanks.

EDIT: But then, is it possible to have Windows and FreeDOS on the same fat32 partition, and be able to choose which one to boot into? I need to have something like that for my older system. The MS-DOS in Windows 98 can't play DOS games as nicely as FreeDOS, it seems. It would be a waste of disk space to make separate partitions for them.

---

### Post by Githlar on 2007-11-18
In installed FreeDOS just so I could play Elder Scrolls Arena, and I can't get it to work, however the error I got was some kind of extended memory issue. I tried tweaking all kinds of things to no avail.

In response to your question, if you want to boot FreeDOS from GRUB, use this menu entry:

title		FreeDOS
map		(hd0,0) (hd1,2)
map		(hd1,2) (hd0,0)
rootnoverify	(hd1,2)
chainloader	+1


(hd1,2) is where my FreeDOS partition is. You're will probably be different. Use:
"find /fdconfig.sys" in the GRUB prompt to determine which partition it is.

---

