---
title: "Install CD ISO image: &quot;Invalid or corrupt kernel&quot;"
date: 2006-02-09
forum: Desktop Environments
---

### Post by alquimista on 2006-02-09
Hi,
I downloaded the Install ISO image for v5.10, from Kubuntu web site. I burned a CD-RW using Nero, and when restarted the laptop (Toshiba Satellite A60) using the CD, I got the initial screen of Kubuntu installation, yet when I pressed "enter" to proceed with the install I got "Invalid or corrupt kernel".
I downloaded the ISO again, burned the CD and I got the same error.

Any help?

Thank you,
Guillermo

---

### Post by zxee on 2006-02-09
Did you google that error message? Seems like alot of the hits from the brief search I did were mentioning grub. [http://www.google.com/search?q=Invalid+or+corrupt+kernel&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial](http://www.google.com/search?q=Invalid+or+corrupt+kernel&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial) Also have you have checked the downloaded image with MD5sums. Maybe you can check the last disc you burned on another computer? Sorry I can't be of more help.

---

### Post by alquimista on 2006-02-09
Thank you for your answer, and sorry for my ignorance but what "MD5sums" is? As I googled it is a .exe file I can use to check consistency in the ISO file I downloaded?
What is strange for me is that in both downloaded processes I got the same error when trying to boot the CD; could it be the CD-RW? should it be a plain CD-R? 
By the way, I have 4 partitions:
1- Kubuntu Hoary
2- Swap
3- FAT32 (for file sharing)
4- WinXP NTFS

I wanted to upgrade Kubuntu from scratch; could partitions interfere in the cd boot process?

Thank you,
Guillermo

---

### Post by alquimista on 2006-02-10
Problem Solved: burn speed was at 10x; I modified it to 4x and now the CD works ok. This solution was thanx to a positing in [http://kubuntuforums.net](http://kubuntuforums.net)

Guillermo

---

