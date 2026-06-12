---
title: "Startup Shutdown Missing Buttons in XGL - Official Thread"
date: 2006-07-20
forum: Desktop Environments
---

### Post by jdusablon on 2006-07-20
From those involved in [this]("http://ubuntuforums.org/showthread.php?t=192871&highlight=start+shutdown+buttons") discussion. This thread is for those having the following problem:

**Missing Shutdown/Restart Buttons in 'Quit' dialog**
(see attachment at thread end, thanks adam.tropics for pic)

This problem affects those using XGL **and** having set up a seperate login session for XGL/Compiz.

**NOTE** This issue does not regard the Startup/Shutdown buttons in GDM (Login Screen,) nor does it regard a missing/non-functional Quit icon.

**Please submit only possible solutions, not simply confirmation of problem**

---

### Post by x64Jimbo on 2006-09-11
It's been a long time. Hasn't anyone found a fix for this yet?

---

### Post by zoetrope666 on 2006-11-10
Hi, 

I've had a similar issue. I don't know if what I'm going to paste below is exactly what you need, but going by your attached thumbnail I can see that we've experienced a similar problem - I too had a 'quit' window like that without the restart and shut down options. I just posted the following info into the main 'Desktop Environments' forum, however I thought I'd post it here too in the hope it might help you out. Good luck!

---

Hi, 

After downloading and trying out some different login window styles for my Ubuntu 6.06 system, I somehow managed to lose the 'shut down' and 'restart' options from both my login and quit application windows. This meant that I had no way of shutting down or restarting my computer, other than by manually holding down the power button. After scouting around online I finally found a solution, however I had to compile info from a range of sources to finally get it resolved. I noticed that a few people around the place have had a similar issue as well, so I thought I'd post my way of solving this problem here in the hope that others might find my post and save themselves some time! 

1. Open a terminal. Type in 'gksudo nautilus' to make yourself root. Your 'Home Folder' browser window will pop up. 
2. Navigate to the 'file system' folder (located on the left).
3. Open the 'etc' folder.
4. Open the 'gdm' folder.
5. Open the file 'gdm.conf-custom'
6. Scroll down to the bottom of this file. If you have a line called 'SystemMenu=false', delete the 'false' part and type in 'true' ( i.e. the new entry should read: SystemMenu=true )
7. Click 'Save'. 
8. Shut off the window.
9. Restart your computer.


This returned the 'shut down' and 'restart' buttons on both my login and quit windows immediately upon restarting my computer. 

I hope this will be of use to someone. :D 

Cheers,
zoetrope.

---

### Post by xvladi on 2006-12-07
Has anyone found a fix for the same problem in KDE (Kubuntu 6.10)?

---

### Post by AusIV4 on 2006-12-08
I haven't found anything for KDE, but believe me, I'm looking. Beryl is freaking awesome, but I'd like to be able to shutdown my laptop properly as well.

---

### Post by AusIV4 on 2006-12-09
I have the answer! This worked for me (and Beryl is running more smoothly now).

Last time, I used method A as described on this page: [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl").

Initially when I tried method C, KDM would not start. Turns out it's an issue of X timing out. This page ([http://wiki.archlinux.org/index.php/Xgl#KDM]("http://wiki.archlinux.org/index.php/Xgl#KDM")) describes a few lines to put into your kdmrc file to prevent timeout errors.

Locate the [X-*-Core] section (of kdmrc) and add the following lines

#Xgl extra lines
OpenRepeat=5
OpenDelay=15
OpenTimeout=2000
ServerTimeout=60

Once I added this my system booted properly to Xgl.

Also note, that you should now select the KDE or Gnome sessions, not the Xgl session described in method A.

---

### Post by manutdfan2850 on 2007-01-05
> **zoetrope666 said:**
> Hi, 

I've had a similar issue. I don't know if what I'm going to paste below is exactly what you need, but going by your attached thumbnail I can see that we've experienced a similar problem - I too had a 'quit' window like that without the restart and shut down options. I just posted the following info into the main 'Desktop Environments' forum, however I thought I'd post it here too in the hope it might help you out. Good luck!

---

Hi, 

After downloading and trying out some different login window styles for my Ubuntu 6.06 system, I somehow managed to lose the 'shut down' and 'restart' options from both my login and quit application windows. This meant that I had no way of shutting down or restarting my computer, other than by manually holding down the power button. After scouting around online I finally found a solution, however I had to compile info from a range of sources to finally get it resolved. I noticed that a few people around the place have had a similar issue as well, so I thought I'd post my way of solving this problem here in the hope that others might find my post and save themselves some time! 

1. Open a terminal. Type in 'gksudo nautilus' to make yourself root. Your 'Home Folder' browser window will pop up. 
2. Navigate to the 'file system' folder (located on the left).
3. Open the 'etc' folder.
4. Open the 'gdm' folder.
5. Open the file 'gdm.conf-custom'
6. Scroll down to the bottom of this file. If you have a line called 'SystemMenu=false', delete the 'false' part and type in 'true' ( i.e. the new entry should read: SystemMenu=true )
7. Click 'Save'. 
8. Shut off the window.
9. Restart your computer.


This returned the 'shut down' and 'restart' buttons on both my login and quit windows immediately upon restarting my computer. 

I hope this will be of use to someone. :D 

Cheers,
zoetrope.

Thank you !!!! i had this problem for so long and i couldnt figure it out.

thanks a lot,  :D

---

### Post by bluefightingcat on 2007-10-25
Hi,

Does anybody have a solution for this in Kubuntu Gutsy? It seems things have changed a bit since feisty and the advice in this post will not work. 

BFC

---

