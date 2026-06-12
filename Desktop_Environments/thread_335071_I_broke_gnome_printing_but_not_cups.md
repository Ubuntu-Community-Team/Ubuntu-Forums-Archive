---
title: "I broke gnome printing but not cups"
date: 2007-01-09
forum: Desktop Environments
---

### Post by mpickett on 2007-01-09
I am using 6.10 and today I installed cups-pdf according to the instructions located on:
[http://www.ubuntuforums.org/showthread.php?t=188860](http://www.ubuntuforums.org/showthread.php?t=188860)

I already had a laserjet 4000 network printer working perfectly when I did this and cups-pdf started working perfectly afterwards.  Unfortunately it seems that I broke the laserjet which no longer works when I print through gnome.  The laserjet does work when I print a test page through cups via the http server ([http://localhost:631)](http://localhost:631)).  It also works when I print via the command line with lpr.  However nothing happens when I try to select the laserjet and print using gnome (i.e. trying to print out a web page with firefox) no errors and no printing.  cups-pdf does work when I do this.  I cannot print a test page using the administration gui in gnome.

I would like to get both working simultaneously or find an alternative to cups-pdf for printing from any gnome application to a pdf.

Any suggestions?

Thanks for the help!
Matthew

EDIT:
I should have tried this first but the problem went away after a restart.  I guess the cups server had to reset...

---

### Post by scrooge_74 on 2007-01-09
You can restart anything by issuing the correct command from /etc/init.d

like sudo sh cupsys restart

---

