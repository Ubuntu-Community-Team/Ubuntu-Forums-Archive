---
title: "Ncurses in virtual console"
date: 2006-04-06
forum: Desktop Environments
---

### Post by ijanos on 2006-04-06
Ncurses based console apps (eg: Aptitude, Mp3blaster) look strange in virtual consoles (Ctrl-Alt-Fx). The main problem is that the line-characters not shown, (BTW is there a way to make a "screenshot" of my console?)

Another problem in terminal is &#369; a &#337; characters don't show in the deafult font, i could change that with *consolechars -f iso iso02.f14* but that's not parmanent :(

---

### Post by ijanos on 2006-04-10
UTF8 bug. After a *sudo unicode_stop* it works fine. Unfortunetly then the &#369;áé&#337; keys draw out more charachters :(

---

### Post by Cashel on 2006-04-11
Yes I had this problem too.. I think I ended up changing my locale from en_US-UTF8 to en_US... I notice now that I've installed dapper the issue is resolved..

---

### Post by ijanos on 2006-04-11
Then maybe an ncurses backport can help us till june :-k

---

