---
title: "No splash screen, takes ages to boot"
date: 2009-03-28
forum: General Help
---

### Post by jezza1972 on 2009-03-28
Ubuntu 8.04. I installed ubuntu about 3 months ago and all was well. The only gripe was the screen resolution which i sorted by using applications->other->screens and graphics. Since then i have no splash screen, only a plain black screen. At the same time it took around 2 minutes to get to the log in screen, after that all was fine.

In the end i reformatted and reinstalled, but even with the fresh install i still have no splash screen and have long boot times. Can anyone help?

---

### Post by Neo_The_User on 2009-03-28
Yes I can.

Terminal:

```

sudo apt-get install rcconf

```

turn off everything you don't need. also, turn off the frame buffer on boot to see if its actually hanging. Turn off the klogd stuff and syslog. cups is pointless too. For desktops, turn off laptop-mode. XD

Also, if you compile a kernel around 800K using the 2.6.22 kernel with pretty much everything turned off except for the critical stuff and optimize the makefile and the config file for your processor and turn off the -g CXXFLAGS and CFLAGS then add -fomit-frame-pointer -s and then you can add -O3 if you like as well along with all debugging stuff turned off in the config for the kernel and don't forget to set the timer frequncy to 1000 Hz. happy booting!

---

### Post by jezza1972 on 2009-03-28
I'm new to this so i hope you're patient lol, Done sudo apt-get install rcconf in terminal, what do i do now?

---

### Post by jezza1972 on 2009-11-12
I found the issue, i was using the onboard graphics. It went t*ts up so i fitted an nvidia graphics card. No more problems.

---

