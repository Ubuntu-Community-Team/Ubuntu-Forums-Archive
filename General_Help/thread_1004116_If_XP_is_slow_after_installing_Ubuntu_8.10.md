---
title: "If XP is slow after installing Ubuntu 8.10"
date: 2008-12-06
forum: General Help
---

### Post by clay7 on 2008-12-06
Just want to pass on some help.

I had a box with XP SP2, 1 G RAM, 160 GB HD and installed a separate HD (40 GB) for 8.10. So, I have one operating system on each drive. Both drives are SATA.

After being a total geek and staying up for 30 hours playing with Ubuntu (love it!), I rebooted to XP. Yikes. It took 10 minutes to pull up when it normally takes 2 minutes at most. I tried copying a 30kb text file from the hard drive to a USB flash drive (USB2) and it took 40 seconds, when normally it's done in a fraction of a second.

Here's what i did to fix it: 
In XP, right click on My Computer, go to Properties, Advanced, and under Performance click Settings. Click the Advanced tab and under the Virtual memory, click Change. Select the option System Managed Size. Then OK your way all the way back out and then restart.

This allows the paging to work more efficiently. Ubuntu calls this the "Swap partition" and they both have the same function.

Hope this saves someone from pulling their hair out.

---

