---
title: "GRUB error 22....d'oh!"
date: 2009-06-05
forum: General Help
---

### Post by shrimpy89 on 2009-06-05
I've dual-booted Vista and Ubuntu for quite awhile now, and I wanted to try Kubuntu.  I installed it on another partition, giving me three OS's and two swap partitions.  GRUB recognized Kubuntu as the "primary" OS.  But KDE didn't charm me all that much, so against what should be common sense, I just deleted its partition (and its swap partition).  So now I have GRUB error 22, preventing me from loading either Ubuntu or Windows.  Since the problem has to do with GRUB, can I use my live CD to edit my GRUB config files and comment out the (deleted) Kubuntu options or something similar?  I've looked up the error on the forums, but they all seem to be about fixing Windows MBR back to default.  Would that mean reinstalling GRUB to access my Linux partition?  

...Sorry, I have lots of questions about this, but I'm exploring and learning Linux--one catastrophic mistake at a time.

---

### Post by ronparent on 2009-06-05
My guess is that when you installed Kubuntu you reset grub to look for grub on the former Kubuntu partition. In any case you can use the live cd to properly configure grub. Booted to the live cd start **sudo grub** from a terminal and do the following series of commands:

>**find /boot/grub/stage1**

Use the output from the output of the above in the following:

>**root (hdx,y)**
>**setup (hdx)**

If you want to examine or edit the grub menu **quit** grub and:

**sudo gedit /boot/grub/menu.lst**

Save any changes and you should be good to go.

---

### Post by shrimpy89 on 2009-06-06
Got it running again! Thanks!  Would you mind explaining what each command did?

---

### Post by philcamlin on 2009-06-06
cool now mine works too !
i did the same as you except i had xp 
:popcorn:

---

### Post by ronparent on 2009-06-06
Gladly. 

The grub command **find /boot/grub/stage1** finds  your grub files usually in the partition where your system is installed and outputs the location of the drive in grub terms. That location is your system root which you enter into the **root** command. You then use the only the drive location from that output (which includes drive, partition) to instruct grub to **setup** or write the mbr on that drive. That mbr (master boot record) contains a small amount of code whose only function is to 'find' the full grub code written in the stage1 and stage2 files which actually writes the grub menu to your screen and executes the loading of whichever operating system you have selected to boot to.

It gets more complicated than that if you have more than one grub/ubuntu installation on separate partitions or separated disk, or, if they are not located on the boot drive selected in bios. If you are going to make it more complicate, then you should study the grub page ([http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)).

Otherwise that is pretty much all you need to setup grub. Have fun.

---

