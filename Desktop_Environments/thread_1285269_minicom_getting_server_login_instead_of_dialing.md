---
title: "minicom getting server login instead of dialing"
date: 2009-10-07
forum: Desktop Environments
---

### Post by jm2 on 2009-10-07
I am using intrepid 8.10. kernal 2.6.27-14.
I have a modem on this machine to be able to dial into this machine. I have installed mgetty and this works just fine.
 
Now, I need the ability to dial out using a modem of this machine using ppp to another machines modem that has SCO 6. (Not the internet) When I do the wvdial doesn't  dial.
 
I tried minicom to see if I can dial out, and I get my ubunutu login message, and it just stays there with several blank lines.
 
(yes, my modem is configured correctly. It used to dial out before I installed the mgetty stuff.)
 
My best guess is because I have the mgetty on. 
 
Is is possible to have a ppp connection with a mgetty on the same serial port? if so, how.
How do I get rid of the mgetty (temporarily so I can do the ppp), if this is my problem?
 
Thanks in advance.

---

### Post by jm2 on 2009-10-12
Since Ubuntu uses event.d instead of inittab. I was not able to turn off the ttyS0 port using inittab.
 
However, the initctl command works for me. 
 
sudo initctl list (shows the processes started in event.d)
 
sudo initctl stop ttyS0 (gets rid of the getty in ps -ef | grep ttyS0) 
 
now I can dial out using minicom.
 
Then when I want to be able to be able to accept dial in calls again:
 
sudo initctl start ttyS0 (re-creates the getty in ps -ef | grep ttyS0)
 
This is part of the Upstart which is replacing the inittab file.

---

