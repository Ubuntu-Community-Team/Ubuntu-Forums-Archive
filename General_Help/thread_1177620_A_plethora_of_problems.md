---
title: "A plethora of problems"
date: 2009-06-03
forum: General Help
---

### Post by maheshjr2000 on 2009-06-03
The BIG one: I installed windows after linux and used the guide to try and restore grub. Unfortunately grub refuses to boot the windows one. Here is the results.txt from bootscript: [http://pastebin.com/d23ef545f](http://pastebin.com/d23ef545f) Also I installed windows on sda3 why does it say that sda2 has the windows boot stuff?

The little ones:
Windows XP didnt install the neccessary drivers.. I need the realtek 8101E drivers but the realtek website doesnt have them that I could find. 

I can has help?

---

### Post by merlinus on 2009-06-03
From what I can see, windows is installed on sda2.  So you will need to change this bit in /boot/grub/menu.lst  (the section that begins with title Windows XP)
rootnoverify (hd0,0) 
makeactive
chainloader +1

to:  

title Windows XP
rootnoverify (hd0,1)
makeactive
chainloader +1

if is indeed on sda3, then the line should be changed to:

rootnoverify (hd0,2)

---

### Post by maheshjr2000 on 2009-06-03
THAT WORKED XD thanks VERY much, I found the driver too!

---

