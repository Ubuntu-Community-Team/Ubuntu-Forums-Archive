---
title: "Emergency help needed"
date: 2006-09-29
forum: Desktop Environments
---

### Post by mykrob on 2006-09-29
I have a friend who is running Ubuntu at his pharmacy, he uses DosEMU to be able to run a lot of his older applications within one system, since XP doesnt have true dos.

Anyway, he had a hard drive failure on one of the systems. We were able to image the drive, minus a few sectors.. Ubuntu will boot to a console, Xorg is messed up, presumably some of it is missing due to the hard drive crash. I have read in the forums where you can repair an Ubuntu install with an apt-get command.. However, the command apt-get is missing from /usr/bin!!

I am not in front of the computer, but i have tried to talk the guy by phone how to copy the files from a live installation. We are unable to get write permission for some reason. I had him mount the drive to a folder

sudo mount /dev/hda1 /home/ubuntu/folder

then try to copy the files

sudo cp -R /usr/bin/* /home/ubuntu/folder/usr/bin


but it will not work..

My question is, is there any way to do a repair installation with Ubuntu? If you no longer have access to apt, what can you do??

If it matters, the file system is xfs

thanks,
-myk

---

### Post by aarbear26 on 2006-09-29
Well, i don't know about howto go about mounting it and that stuff, but if you use the Ubuntu Alternate install CD, it does give you an option to rescue a broken system. I've never done it myself, but it may get you started.  Good luck!

---

### Post by Houman on 2006-09-29
Why dont you install the broken harddrive as a secondary hd in a computer running a working OS and just try to rescue as many files as you can,

I dont see why youre trying to boot from the bad hd, 

regards
Houman

---

### Post by mykrob on 2006-09-29
we are booting from the new hard drive and have resuced as much as we can.

---

