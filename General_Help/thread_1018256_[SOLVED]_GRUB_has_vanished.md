---
title: "[SOLVED] GRUB has vanished"
date: 2008-12-21
forum: General Help
---

### Post by Flaphal on 2008-12-21
I normally dual boot Ubuntu and Vista, a couple of days ago I decided to try KDE with openSUSE. Everything was working fine, until today after I booted into Vista GRUB no longer loads when I restart the laptop- it loads straight into Vista. 

How can I bring back the GRUB menu?


Possibly important- after installing openSUSE I got what appeared to be two GRUB menu's. The one SUSE installed, and my original menu that would be loaded by selecting Ubuntu from SUSE's menu.

Not sure if this is the proper place to ask, as I don't think this is really an issue with Ubuntu, but I thought you guys might be able to help.

Cheers

---

### Post by unutbu on 2008-12-21
How about try these instruction to reinstall GRUB:
```
http://ubuntuforums.org/showpost.php?p=1308395&postcount=1
```
If you run into any problems or question, please post the terminal commands you had used up to that point.

---

### Post by IEKnight on 2008-12-21
I hope this helps:

[LIST=1]
[*]Boot your computer from the Live CD
[*]Open up a Terminal
[*]*sudo grub*
[*]*find /boot/grub/stage1*
[*]*root (<output from the last step>)* - should look something like root *(hd0,1)*
[*]*setup (hd0)*
[*]*quit*
[*]restart the computer
[/LIST]

---

### Post by Flaphal on 2008-12-23
Thanks guys, that solved it in less than 5 minutes :)

---

