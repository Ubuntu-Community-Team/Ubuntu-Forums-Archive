---
title: "Need A Partition Of Linux (ubuntu)!!!"
date: 2007-10-23
forum: Desktop Environments
---

### Post by xoron on 2007-10-23
hi

i am a windows user and a bit of a ubuntu user and i want to be able to use both. i know what a partition is but i dont know how to go about doing it.

in my head the simplest way of doing is you put windows on one hard drive and ubuntu on the other (i already have 2 hard drives) then to select different OS i can change the BIOS boot order.

is this possible?

i would also like to know how to make a partition that can be used by linux as well as windows, because linux will not be using much space (its uses are sumwhat limited to security issues...windows security sucks!!!)

:):):)

thanks in advanced for your help :)

---

### Post by pbcartwright on 2007-10-23
if you have a computer with 1 or 2 hard drives, you can put ubuntu on it, dual-boot with Windows XP. I have done that many times.
when you start the Ubuntu install process you will get to the partitioning section. Here you want to do MANUAL install. Then when it shows you the drives and partitions you have, you can modify them, change them remove them...
If you want to put linux on the 2nd hard drive and leave the first alone you can do that. just select the 2nd HD delete all partitions on it, make 3 new partitions. One for "/" root, one for /home and one for swap. Make swap as big as your current memory, or 1-2 Gb. Make home as big as you want, and make "/" root 10Gb ( or more..)
you could also do a guided install ( I think..) where you just tell it to use one of your HDs.. you can play with it, and it will TELL you when you are done, that it will then write the current setup and format the partitions you select...
remember to always backup important data FIRST :)

---

### Post by xoron on 2007-10-23
with guided install, will i be able change OS through BIOS or will i be given option by computer?

...i have 4GB RAM should i give that much to swap partition...that seems like alot...will it need that much or will less suffice?

---

### Post by xoron on 2007-10-23
BTW i already have windows and so i dont wanna have to re install windows (sooooooo slooooow( compared to ubuntu 15 mins))

if need arises i dont mind but i would like to avoid installing windows scenario.

---

### Post by Sunforge on 2007-10-23
Ubuntu will install a boot loader called GRUB which should recognise the fact that you have a Microsoft and Linux OS installed and give you the option of switching between them at boot time, if both OS's are installed on hard drives permanently attached to your system.

You should be able to boot several OS's at once off different hard drives without a problem, although things get out of hand if you really try hard.

Back in 97 I used to use the BIOS for forcing one OS to boot in preference to another due to the limits of boot loaders, the 1024 cylinder limit and all the rest but now you don't have to pay too much attention to this as long as you let GRUB settle where it needs to which is generally smack on top of the old Microsoft boot loader.

---

### Post by dward526 on 2007-10-23
Being a dual-boot user myself on my main desktop, I also suggest creating a third partition for all your data to be saved to.  The reason why is this, although you can manipulate the windows partition from Ubuntu, windows does respond in kind.  If you save all your documentation to a third partition (this partition used to have to be FAT but can now be NTFS :) ), you can access them regardless of the OS you choose to boot.  I also use this fact because I have as...experimental nature and it will save my data.

---

