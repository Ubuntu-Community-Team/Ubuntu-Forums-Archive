---
title: "Blank screensavers"
date: 2006-09-04
forum: Desktop Environments
---

### Post by sumguy231 on 2006-09-04
Hello, I'm using KDE 3.5.4 on Kubuntu Dapper and after my system shut down uncleanly (but reiserfsck turned out fine) none of the screensavers work. I am able to 'test' them just fine, but when they actually appear on their own they just blank the screen. I have the following screensaver-related packages installed:
[FONT="Lucida Console"]kscreensaver
kscreensaver-xsavers
kscreensaver-xsavers-extra
ktux
xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xcreensaver-gl-extra[/FONT]
Any help would be appreciated if anyone has any ideas, thanks.

---

### Post by sumguy231 on 2006-09-04
Never mind, I did some digging and found a solution in this thread:
[http://www.linuxquestions.org/questions/showthread.php?t=441670&highlight=blank+screensaver](http://www.linuxquestions.org/questions/showthread.php?t=441670&highlight=blank+screensaver)
For future reference, setting DPMS-dependent=false helped to fix the problem for me.

---

### Post by sumguy231 on 2006-09-04
Grumble, double-post...

---

