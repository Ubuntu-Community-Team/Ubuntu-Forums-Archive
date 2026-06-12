---
title: "run SETUP from console - how"
date: 2006-01-06
forum: General Help
---

### Post by Optiker on 2006-01-06
Next noob question...

I avoid command line if possible, however, it's not possible in this case.

I downloaded the free version of TurboPrint because it was the only Linux driver identified for my new Canon PIXMA iP5200 printer. It downloads as a tgz file, and I've managed to get that into a folder in my /home/name/ folder, and the contents extracted.

One of the files is named "setup" and TurboPrint's instructions say to navigate to the folder and as administrator, run it from the console. I changed to that folder, and entered the following...

sudo setup

but got that command isn't known. Then I did a HELP in the console and saw an exec command, and tried that - same result.

Can somebody give me the syntax to run that setup?

Thanks!
Optiker

---

### Post by Susana on 2006-01-06
try sudo ./setup

---

### Post by Optiker on 2006-01-06
Cancel...haven't learned from my mistakes of a half hour or so ago!

If I follow the instructions carefully and type sudo ./setup instead of sudo setup, it works!

Maybe next time I'll be more careful.

Sorry for the bother.
Optiker

---

### Post by Optiker on 2006-01-06
Susana...thanks for the reply...nice to know that what I discovered was actually the correct answer.   :)

Whoa! It actually works! I actually have a printer working on my Kubuntu system! Never thought I'd get there considering that it's a fairly new printer model. Of course, the driver doesn't provide as nice an interface as the Canon driver, and I'm sure some features are disabled in the TurboPrint free version, but it beats nothing.

Haven't tried my other printer yet - an ancient HP Laserjet 1100 - but I'm expecting it will work OK.

These are some of the major hurdles in heading for my default boot being Kubuntu and WinXP being secondary. Still a few to go - including WINE!

Y'all will see me again, I'm sure.

Thanks all!
Optiker

---

