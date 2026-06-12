---
title: "[SOLVED] HP LaserJet 1020 not printing"
date: 2008-10-10
forum: Desktop Environments
---

### Post by gjosef on 2008-10-10
I just connected a HP LaserJet 1020 to my Ubuntu Desktop 8.04 through USB.

Ubuntu detected and identified the printer automatically, but I am not able to print.

When I print a test page, I see the printer icon appearing in the top right corner of the desktop, and if I click on it, I can see the print job there for some seconds before it disappears. But I see no activity on the printer.

Would be grateful for help.

---

### Post by gjosef on 2008-10-10
I found the answer in an earlier thread:

[http://ubuntuforums.org/showthread.php?t=602883](http://ubuntuforums.org/showthread.php?t=602883)

Had to run the command
```
$ sudo hp-setup
```
from the terminal, and then it worked.

---

### Post by ozPATT on 2009-03-17
hasn't worked for me unfortunately... when i run the hp-setup, it says that it has been installed correctly, but when i press finish, it seems to stop there.. doesnt print the test page, doesn't close the setup. 

i have had the printer working really well, but not sure what changed. before, i didn't have hplip, i just plugged it in and ubuntu did the rest, but then that stopped, and thats why i tried the hplip. any suggestions on what I can try next? 

thanks

Patrick

---

### Post by Rasheeke on 2009-10-05
Same.  Printer was working fine after a few kinks getting it working but after dual booting to Vista and back it's now still detected every time I try to reinstall it but never prints the test page.

---

