---
title: "Xorg file problem after Ubuntu fails to boot - HELP!"
date: 2011-01-06
forum: Desktop Environments
---

### Post by Cvrsor on 2011-01-06
Hello,
I am facing the following strange problem and I'd like your help if you can!

I have installed **Ubuntu 10.04** 64bit on my **third Hard Disk Drive** (that is on **/dev/sdc4**) and also have one Sony Monitor 1280x1024 and one LG LED monitor set up with **TwinView** 1920x1080. My graphics card is an **Nvidia GeForce 9800 GT**.

My Ubuntu partition boots up without any problems, but every 3-4 days the following sequence of errors occurs:

1) My second HDD (/dev/hdb) fails every couple of days (it is old).
2) My Ubuntu partition cannot boot. I get an error message "*error: no such device:*" and "*error: no such partition*". My guess, because instead of being recognised as /dev/sdc, it is now in turn /dev/sdb, as the second HDD is missing.
3) When I restart, usually Grub menu appears normally, but then the monitor goes blank and nothing happens.
4) I have found that an out-of-sync error occurs, ALWAYS after the above steps 1 & 2, i.e. when I the second drive fails and I get the no such devise error, the next time an out-of-sync problem occurs.
5) To correct this, I boot from Live CD, delete xorg.conf, place a nearly blank xorg file instead (from here:[http://bit.ly/h5WJbN](http://bit.ly/h5WJbN)) and boot with nomodeset option.
6) I run Nvidia XServer Settings utility, config the monitors from scratch, and save to xorg file. 

Everything runs smoothly for some time, and then the same thing happens again.

My questions are:
1) Should I try and reinstall Ubuntu on the first SATA drive to avoid the above error? Do you think it is related?
2) Why does the xorg file need to be rewritten after Ubuntu fails to boot (see #2 above)? It becomes corrupt?

Any help would be greatly appreciated! I am a bit stuck here with this nasty situation!
Thanks!
Alex

---

### Post by gordintoronto on 2011-01-06
Can you change the order of the drives, so the one which fails is last? Or, even better, replace the failing drive.

I have no idea on the xorg question.

---

