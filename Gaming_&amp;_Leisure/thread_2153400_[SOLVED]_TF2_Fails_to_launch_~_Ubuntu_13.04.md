---
title: "[SOLVED] TF2 Fails to launch ~ Ubuntu 13.04"
date: 2013-06-10
forum: Gaming &amp; Leisure
---

### Post by hking0036 on 2013-06-10
I've had this issue with all versions of ubuntu; when I launch steam, it opens a window that is just black and says Team Fortress 2 [OpenGL]. It will stay a black screen, until I kill the process through task manager. Is it something to do with my video card drivers, or what?

Computer:

Dell Latitude E6400 w/ Nvidia GTS 160M.

---

### Post by Shrek01 on 2013-06-12
Have you installed the latest driver from Nvidia?

I had TF2 stop launching one day, and that's how I found out that a new version of the driver came out  :D
It seems that Valve uses the latest driver for Linux out there for TF2.

---

### Post by hking0036 on 2013-06-15
Alright, I'll check that out, Thanks :D

EDIT: turned out I was using the noveau drivers. >_< well, thanks for reminding me.

EDT 2: Now when I launch it says "could not find required OpenGL entry point 'glGetError'! Either Your video card is unsupported, or your opengl driver needs to be updated". Do I just update it by doing a sudo apt-get upgrade, or is there some other way? when I went to settings>softwares & updates>Additional I applied the latest driver.

EDIT 3: Rebooted my computer fixed it, solved~

---

