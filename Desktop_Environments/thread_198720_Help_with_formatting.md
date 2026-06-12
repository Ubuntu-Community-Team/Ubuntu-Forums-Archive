---
title: "Help with formatting"
date: 2006-06-17
forum: Desktop Environments
---

### Post by Buecai9ahd on 2006-06-17
Hope this is the right section. If not feel free to move it.

Ok, here is my problem. I recently tried to install Windows XP on my hard drive. Anyway the computer restarts itself to complete the setup, but when it did there was an error and it said it needs to be restarted. But it just keeps doing this cycle forever!!
Anyway, I need to get it reformatted but I can’t even get into DOS etc. So I thought I would use trusty Linux Live CD to format the HDD. Trouble is, I’m new to Linux so I don’t know too much about it.
Could someone tell me what to do, step-by-step to get it formatted? I presume it will be C drive? Or should I use a command to check all my drives first? 
Thanks for any help you can give a Linux newbie!

Oh and are the commands any different for different Linux distro's?

---

### Post by ajgreeny on 2006-06-17
We could do with more information about the machine you have (disk or disks etc) and what OS's you intend to install.   If you only want windows and just need help with formatting for windows, then I think the windows installer should do it all for you without too many problems.  If you want windows as well as Ubuntu, you should install windows first, then add Ubuntu to the system.  This makes life a lot easier, as if you install windows after Ubuntu you will lose your grub boot manager and have to reinstall that to get Ubuntu up and running.

Let us know what you intend to do with the computer and I'm sure you will get help.

---

### Post by Buecai9ahd on 2006-06-17
No problem, and thanks for the quick reply. For the moment, I would like to just figure out how to format my HDD from Linux live CD and actually get it working first! There's one HDD and it used to have Win 98SE until I tried upgrading. 
As I say, it's stuck in a continous cycle of trying to finish the setup when there's an error, then it reboots and it carries on. 
I can't access the DOS by pressing F8 because the options not there, so I figured Linux would be the best bet to first format the drive, get Windows installed and then install Linux after (let's face it, Windows does kind of suck and it's very unstable).
I'm not familiar with the commands in Linux. I've searched but there seems to be hundreds of different commands for the same thing!
It's a pretty old PC as well.
Cheers

---

### Post by ajgreeny on 2006-06-18
OK, Lets just check.  You want to install windows and then linux (Ubuntu)?

If that is the situation, then just go ahead with the windows install CD and do that first.  If this is where the problem is then I'm afraid I don't know of any way I can help, other than suggesting that you use the Ubuntu Live CD and go through the install process untill you get to the format part.  Make sure you set the disk to format as DOS, and do this but then when you have formatted just shutdown and do not install Ubuntu.  Now try restarting and installing windows without formatting if that is possible, I can't remember exactly the sequence that windows puts you through, (you will already have a dos formatted partition available).  If that goes OK, then you can install Ubuntu, and reformat the appropriate size of the disk to ext3 for the linux OS.

Sorry if that is a bit convoluted, but if you are having trouble with windows instalation, I'm not quite sure where to suggest you look for further help.

---

### Post by german640 on 2006-06-18
If you want to format to install Windows XP, just start again from the Windows XP install CD and delete the old partition, create a new one (just the necessary space for Windows, you must create another partition later to share files between Windows and Ubuntu), format it and install Windows.
After that you can boot from de Ubuntu CD and install Ubuntu creating 3 new partitions: One for Ubuntu with ext3 format, one for sharing files between Ubuntu and Windows with Fat32 format, and one swap partition.

Hope it helps

---

