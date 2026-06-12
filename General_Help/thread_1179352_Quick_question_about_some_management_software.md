---
title: "Quick question about some management software"
date: 2009-06-05
forum: General Help
---

### Post by devnull123 on 2009-06-05
I am planning on dual-booting Ubuntu with Windows XP...and in order to do that I need to create a new partition...anyway just to make sure I have enough space on my HDD and RAM and all that fun stuff, I was wondering if someone could point me to a piece of software that allows me to see my system specs (like PC Wizard does for windows).


Thank you for your time


PS Im using Ubuntu 9.04

---

### Post by ajgreeny on 2009-06-05
For a gui you should install **hwinfo**, or you can just use **lshw** in terminal.  If you use the command ```
sudo lshw >hardware.txt
``` a text file will be made in your home folder called hardware.txt which, of course, you can then read with text editor, Gedit.

If all you want is to see your memory and disk sizes and usage you can do both with the terminal.  For memory use ```
free -m
``` and for disk usage ```
df -h
```, but to see your graphics card use ```
lspci -nn | grep VGA
```
There are many other commands you can use, all of which can be very useful.```
sudo fdisk -l
``` will show the partitions on your disk(s) and the OSs they contain with their filesystem types.

---

### Post by devnull123 on 2009-06-05
Thank You...I have all I need

---

