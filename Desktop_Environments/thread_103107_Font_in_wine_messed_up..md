---
title: "Font in wine messed up."
date: 2005-12-13
forum: Desktop Environments
---

### Post by Heavymetalman on 2005-12-13
Hi all, I finally switched completely over to linux and I love it. Ubuntu is the best distro I've tried so far. Anyway, there still are a few programs that I would like to use that are windows only so wine seems to work well in most cases.  I was installing a sheet music transcriber and the install didnt seem to work, but after that whenever I run something in wine the fonts are set to the musical font that came with that program.  So all I see is a bunch of music notes.  How do I change the font back to normal in wine?  I tried using 'winecfg' but that was a bunch of music notes too :(

---

### Post by Heavymetalman on 2005-12-14
nevermind..i figured it out..

---

### Post by bluevoodoo1 on 2006-01-25
I'm having a similar problem as described here...

[http://ubuntuforums.org/showthread.php?t=118876](http://ubuntuforums.org/showthread.php?t=118876)

how did you solve your problem?

---

### Post by lucaflea on 2006-01-25
hi. whitch version of wine did you install? mine doesn't work... i do need only finale!

how did you make it work?

luca

---

### Post by bluevoodoo1 on 2006-01-25
[QUOTE=lucaflea]hi. whitch version of wine did you install? mine doesn't work... i do need only finale!

how did you make it work?

luca[/QUOTE]


I followed [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) to make it work. Seemed like the version in the repositories wasn't working for me either, but adding...

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

to your sources list will let you get wine version 0.9.6.


Now the font problem....

---

