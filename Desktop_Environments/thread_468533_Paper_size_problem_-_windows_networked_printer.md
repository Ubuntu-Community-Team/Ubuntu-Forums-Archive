---
title: "Paper size problem - windows networked printer"
date: 2007-06-08
forum: Desktop Environments
---

### Post by MindFork on 2007-06-08
Printer is on windows machine, and is shared fine with other windows boxes.

Installed printer via cups and have changed every paper size setting from A4 to letter, including /etc/papersize

But whenever I print, I get a message on the windows box "A paper size that cannot be fed from the cassette was selected."

Printer is a Canon PIXMA iP3000.  The rest of the error reads "Load paper in the sheet feeder and press teh Paper Feed Switch on the printer. Then click OK."  But doing that doesn't get any response from the printer.

Any suggestions?

---

### Post by stoli150 on 2007-06-09
sorry I don't have an answer but I'm seeing a similar issue after installing hp print driver default paper size is A4. You need to change that and when another printers prints to the host system they have to change to letter from a 4 as well.

---

### Post by MindFork on 2007-06-09
I'm at it again today, but still no luck.  I tried changing the paper size on the windows machine printer properties to A4 to see if it would print, but I got the same error message.  I checked again that every setting in ubuntu that I know of was set to "letter" -- /etc/papersize, system > administration > printers (both of the printers choices) on every tab...everything says letter, but still no love.

Somebody...?  Anybody...?

---

### Post by MindFork on 2007-06-10
Still haven't been able to print anything.  Anybody have some advice?

---

### Post by MindFork on 2007-06-13
Every single setting everywhere says A4, but I still get the same error.  

Anybody?

Anybody...?

---

### Post by eyoungut on 2007-09-10
I have the exact same problem but with Pixma ip4000 and MP780 printers... do you find anything that worked?

THANKS!

---

### Post by MindFork on 2007-09-11
Nope, I never was able to fix the problem.  If I have to print something, I print it from the windows machine.  :(

---

### Post by David Mulligan on 2007-09-26
I have to guess that the built in repository for this driver is broken.  Has anyone tried to install the driver from the manufacturer?  Has anyone tried this with Edgy?

---

### Post by eyoungut on 2007-10-23
Not sure what Edgy is, but I configured Win XP to support unix printing, added a new LPD printer, and it works fine that way.

---

### Post by David Mulligan on 2007-10-23
Good news.  My upgrade to Gutsy Gibbon solved my printer problems.  Well I did a clean install but still no printer issues anymore.

---

