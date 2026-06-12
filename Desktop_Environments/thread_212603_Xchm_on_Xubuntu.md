---
title: "Xchm on Xubuntu"
date: 2006-07-10
forum: Desktop Environments
---

### Post by dolby on 2006-07-10
i cant seem to be able to get xchm to work on Xubuntu. it just hangs. tried running it through terminal but no errors appeared there too. only time i've ever seen its gui was once when i opened like 5 chm documents & about half an hour later from the time i opened them. anyone else having similar problems?

---

### Post by dolby on 2006-07-29
this problem is solved. something to do with repos probably cause now it installs 5 packages insted of 2 when it didnt work

---

### Post by Spyridon Gouliarmis on 2006-08-06
Well when I installed xchm, it took only two packages (xchm and libchm1, I think), and I had the same problem.  (I already had some wxWidgets packages on my computer, however.)

Apparently on my system it was a cups problem, since after getting cupsd to work xchm ran OK.

Cupsd, however, wasn't the real culprit, since it just wasn't able to set up a socket on 127.0.0.1 : see [https://launchpad.net/products/cups/+bug/31339](https://launchpad.net/products/cups/+bug/31339) .

The only difference between my problem and the one reported in launchpad is that lo wasn't brought up by "sudo ifup lo" because the file /etc/network/interfaces contained some (incorrect) lines put there by pppoeconf.  (pppoeconf itself stopped working correctly some time ago, but I just deleted the lines and didn't investigate further.)

Hope this helps someone.

---

### Post by dolby on 2006-08-06
i just reinstalled it and works now with downloading only 2 packages. dont know what the problem was really. maybe sth with my at the time configuration

---

