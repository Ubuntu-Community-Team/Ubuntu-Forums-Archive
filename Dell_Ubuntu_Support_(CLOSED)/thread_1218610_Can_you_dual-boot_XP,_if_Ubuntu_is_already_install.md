---
title: "Can you dual-boot XP, if Ubuntu is already installed?"
date: 2009-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mammoth245 on 2009-07-20
Recently I just installed Ubuntu Linux. I love it, but most of my favorite programs are Windows only. I want to keep Ubuntu, but I need to dual boot windows. I have a disk from Dell that came with my computer for reinstallation of Windows XP SP2 (Dell Dimension 3000 Desktop) but anytime I load up the disk, I cannot figure out how to install it. When I would reformat (reinstall) XP when I had XP, I would put the disk in, then it would give me a menu screen, now with Ubuntu it gives me otherwise. 

Help please?

---

### Post by utnubuuser on 2009-07-20
Is it an Xp installation disk or just a service pack disk?

---

### Post by Mammoth245 on 2009-07-20
I don't know it came with the computer. It's just a purple disk with some writing on it

---

### Post by mchecca on 2009-07-21
If it is an XP installation CD, then it's easy to set them both up. Use GParted (available in repos) to partition your hard drive. Format the partition you want for XP to be FAT32 and label it WINDOWS or something you'll remeber. Then boot from the CD and when it asks where to install your partition should be letter C: and when it asks to format it make sure you format it as NTFS. install then it should automatically boot into Windows XP. Restart your computer with the Ubuntu CD and run GParted. Open up a terminal and type "sudo grub" then "root (hd0,0)" (or whatever your partition number is) then "setup (hd0)" restart your computer with the CD and it should boot into Ubuntu. Open up a terminal again and type "sudo gedit '/boot/grub/menu.lst' " About halfway down should be an example of a Windows OS like this:[INDENT]# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
[/INDENT]Copy this and paste it as the last line (and remove the # marks), making sure you change (hd0,0) to your partition number. Restart again, press escape, and you should have a choice of both OSs. Sorry this was so long and if you need help with anything let me know.

---

