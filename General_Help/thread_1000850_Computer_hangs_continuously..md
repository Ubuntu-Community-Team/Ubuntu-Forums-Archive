---
title: "Computer hangs continuously."
date: 2008-12-03
forum: General Help
---

### Post by t4ggs on 2008-12-03
Hi, I'm trying to repair my cousin's computer...he wanted windows,he doesn't knows a lot about computers, so I tried installing windows, formated the hard disk and when the computer restarted it was trying to install again, i did the same thing twice and exactly after formating when trying to copy the files to the disk it hangs and restart,... then i went and installed ubuntu intrepid...



everything perfect but after the installation i made the first update and suddenly it hangs, the mouse and the keyboard don't respond....i formated and installed ubuntu once again and then after the first reboot, made the update and it hangs again..so i just restarted and continued the update...used for about an hour and everything was perfect...then i tried to install many firefox extensions (i keep all the xpi in one folder) and when i dropped them all into firefox's addons windows it started to install but suddenly it hanged again.

why is this happening? I ran memtest for about 20 minutes with no error (512 of ram), use Hyren boot disk tested the cpu and its ok, the video and its ok, the disk are fine too...

I don't know why it happens...any idea?

---

### Post by Titan8990 on 2008-12-03
Sounds like a definite hardware issue. Have you inspected the board for bulging capacitors?

---

### Post by t4ggs on 2008-12-03
At sight the mobo and all the components seems allright...

I've been looking in the system log, but i dont understand anything...where should i look, there is auth daemon debug kern messages syslog user xorg.0

---

### Post by Titan8990 on 2008-12-03
Typically, I start with syslog and dmesg. Feel free to post them here.

---

### Post by Dark Hornet on 2008-12-03
If your computer is hanging as in freezing...you might want to boot up into your bios and check your CPU temp, and monitor that for a few min.  I had this issue the other day with an old box of mine...2 min after boot up, my box would just freeze...turns out my CPU heat sync was having issues, and the CPU was overheating and causing the box to freeze.  Just a thought...good luck!

Darkhornet

---

### Post by t4ggs on 2008-12-03
The cpu temperature is 35 degrees celsius, 90 farenheit..
so its ok...

what is dmesg?
the computer hanged at 20:07:03
 in the attached file there are 3 pics showing the log...

thakn u for your help.

---

### Post by t4ggs on 2008-12-05
any idea??? could it be the power supply?

---

