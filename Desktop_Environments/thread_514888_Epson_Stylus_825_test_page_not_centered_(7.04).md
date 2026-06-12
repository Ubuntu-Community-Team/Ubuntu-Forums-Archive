---
title: "Epson Stylus 825 test page not centered (7.04)"
date: 2007-08-01
forum: Desktop Environments
---

### Post by wkulecz on 2007-08-01
Just setup Ubuntu 7.04 for my wife to replace a Windows2000 I couldn't restore after a motherboard failure.  So far so good,  but a few issues remain.

Installing the Epson Stylus Photo  825 USB printer was a piece of cake, except the test page printout is not centered and runs off the bottom.

I had this problem with the HP LaserJet 2100m at work using 6.06, but changing the paper size under the printer properties paper tab from A4 to letter fixed it.  Unfortunately this change had no effect on the Epson 825 under 7.04.

I'm using the default recommended driver.  Solution?

--wally.

---

### Post by pedrogl on 2007-08-02
Hi, I also had strange problems with paper size, fixed some of them by replacing A4 with letter in the file /etc/papersize
Hope it helps

---

### Post by wkulecz on 2007-08-02
Good suggestion, /etc/papersize was a single line a4 I changed it to letter, no help.  I'd already tried changing the paper setting in the properties window from A4 to letter.

I printed a web page and the printout was centered so it looks like this is just a bug in the "print test page" function.

--wally.

---

