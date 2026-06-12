---
title: "I need to go back &quot;single boot&quot; on my desktop"
date: 2005-10-01
forum: Desktop Environments
---

### Post by tank45 on 2005-10-01
I've been dualing booting on my desktop now with an extra 20gig HDD. I want to get it back to being my second hdd on the Windows side. I can easily reformat  the hdd using the built in windows disk management but im worried i may screw something up and my computer wont boot I have had some problems with grub loaders in the past. Well hopefully someone understand what I'm saying and can point me into the right direction. I haven't ditched linux completely I still dualboot on my laptop :razz:

---

### Post by aysiu on 2005-10-01
Just edit the /boot/grub/menu.lst and change *timeout 10* to *timeout 0* and *default #* to the default number that Windows is in the list (keep in mind the numbering starts with 0).

---

### Post by hkl8324 on 2005-10-01
insert the floppy windows boot disk and issue

fdisk /mbr

at the DOS prompt.

---

### Post by tank45 on 2005-10-01
I don't have a floppy drive >_< I can just use a windows cd and go to the console and type fixmbr and it should do the same thing? correct and then the second hdd should show up in the windows explorer?

---

### Post by aysiu on 2005-10-01
[QUOTE=tank45]I can just use a windows cd and go to the console and type fixmbr and it should do the same thing?[/QUOTE] [Microsoft has instructions on this](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)

---

### Post by hkl8324 on 2005-10-01
Oh..i missread something...
do you want to 
1.get rid of Grub loader?
2.claim back the second HD?
if yes, yes you can insert the Windows XP cd and type fixmbr, it is the same thing as fdisk /mbr with the floppy. This will fix problem 1.
How to claim back the second HD? Just use the disk management tool in Windows Control Panal is OK. This solves problem 2.

---

### Post by tank45 on 2005-10-01
Alright i just did the command im now back up the computer I got really nervous there for a few seconds thinking oh crap im screwed but it all goes well. Much thanks to you guys

---

