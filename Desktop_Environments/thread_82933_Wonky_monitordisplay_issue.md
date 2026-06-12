---
title: "Wonky monitor/display issue"
date: 2005-10-27
forum: Desktop Environments
---

### Post by gramiq on 2005-10-27
Hi... I just installed Ubuntu 5.10 for the first time, switching over from Yoper. I'm by no means a linux pro, but I'm not terrified of the command line and can follow instructions.

I'm dual-booting my machine with WinXP, and have configured everything nicely the way I want it except for one weird little problem:

Every time I boot into Ubuntu, the screen 'slides' over about half a cm on my monitor. It's just enough to be annoying, as it cuts off the "M" of the AM/PM bit of the clock and half of the Trash Can.

I can fix it easily by adjusting the display position on the front of my monitor, but when I boot back into Windows, the screen has slid over to the left now.  So it appears that Windows and Ubuntu just have a slight variance as to where they tell the moitor to display the desktop.

I suppose I could cure it permanently by narrowing the width of my display using the front monitor buttons, but that feels like giving up, and I'd prefer a real solution.

My monitor is a Samsung SyncMaster 950b and I can post my xorg.conf here if anyone thinks it will help, but it appears to be configured properly.

Thanks!

---

### Post by jeremytaylor on 2005-10-27
try using xvidtune to generate a modeline that puts your display in the right place. Once you've got that you can insert it into your /etc/X11/xorg.conf file to make the change permanent.
hope that helps
Jeremy

---

