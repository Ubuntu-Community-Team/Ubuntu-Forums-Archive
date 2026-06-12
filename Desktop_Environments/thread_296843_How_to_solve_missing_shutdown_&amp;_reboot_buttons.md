---
title: "How to solve missing shutdown &amp; reboot buttons on login &amp; quit windows problem."
date: 2006-11-10
forum: Desktop Environments
---

### Post by zoetrope666 on 2006-11-10
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

### Post by i386geek on 2006-11-10
Thanks for the tip. I'm able to restart and shutdown now with my edubuntu 6.06 system.

---

