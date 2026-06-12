---
title: "Dell XPS 1530 Mouse not working"
date: 2008-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lovelyvik293 on 2008-12-07
Hi,
I have a dell xps 1530 laptop yesterday i installed the ubuntu 8.10.All things are working great,but not the tochpad,when i connect a mouse,the mouse works great.

Please help me to resolve this problem.

---

### Post by falcon61102 on 2008-12-07
Open up a terminal and run the following command to open your GRUB menu.lst
```
gksudo gedit /boot/grub/menu.lst
```

Once that opens, scroll down to the bottom of the screen and you will see the list of your kernal versions.  You should also see that each one has a line that begins with kernal.  Copy and paste the follow code at the end of each line, save the file and then restart:
```
i8042.nomux=1
```

Your touchpad should now work on restart.

---

### Post by lovelyvik293 on 2008-12-07
Thanks a lot.It's working great now.
Is it any bug or what and i wanna know what that code did?

---

### Post by falcon61102 on 2008-12-07
That's a known issues with many Dell laptops.  And as far as what that code specifically does, I really don't know.  I know it's enabling something but I forget exactly what.  I'm sure if you looked around you'll find out some more info on it.

One other thing, keep that line in mind the next time you do a kernal update.  The kernal update will also update your GRUB menu and it should put that bit in there but it's good to check to make sure.

---

### Post by lovelyvik293 on 2008-12-07
Ya i know the update thing.
Thanks one more time.:popcorn:

---

### Post by falcon61102 on 2008-12-07
No problem, glad you got it working.

---

### Post by dphurst on 2009-01-09
The ALPS touchpad does not vertically scroll.  The Xorg.0.log shows that the Synaptics Touchpad is not found.  The evdev driver is loaded.  SHMConfig is true in my xorg.conf.  I have the kernel option i8402.nomux=1 in the menu.lst file as stated.

The machine is a XPS M1530 N series just acquired from Dell with 8.04 preinstalled but not 8.04.1.  Initially the touchpad vertical scroll worked when the laptop was first booted.  The Ubuntu updates that were required to bring the laptop up to date broke the touchpad scrolling.  I tried fixing it by switching kernels from the generic to the 386.  That actually worked, yet lost the multi-core functionality.  Anyway, I'm back to the generic kernel.

Any ideas on why the synaptics touchpad driver isn't loaded?  I've read quite a bit of different threads on this topic.  Some are fixed by modifying and rebuilding the alps driver.  Others are fixed with kernel option mentioned above.
Thanks for your help,
Dow

---

