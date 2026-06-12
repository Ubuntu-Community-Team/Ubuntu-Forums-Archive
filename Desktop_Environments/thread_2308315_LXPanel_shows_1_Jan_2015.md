---
title: "LXPanel shows 1 Jan 2015"
date: 2016-01-01
forum: Desktop Environments
---

### Post by Charlotte18 on 2016-01-01
If I use the date command in the terminal, I see 01/01/16, but LXPanel 0.7.2 task bar incorrectly shows "Fri 1 Jan 2015." If I click on the date on the task bar, the calendar which appears shows January 2016 correctly. Any ideas?

---

### Post by Charlotte18 on 2016-01-03
I fixed this issue by replacing %G with %Y in the digital clock settings, but I still can't figure out why %G shows the year as 2015.

---

### Post by meltingpot2015 on 2016-01-03
If you revert to %G now, the lxpanel digital clock should say 2016. (Of course you will then have the same problem on 01 Jan Next year, when it will say 2016, so best to go with %Y). May have had something to do with the first Monday (today) of this year starting on the 04 January 2016. The [ubuntu help website ]("https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock")(which you may have already seen) says this:


%G is replaced by a year as a decimal number with century. This year is the one that contains the greater part of the week (Monday as the first day of the week)


Very interesting though..just need to make sure I write 2016, when not working on Computer, on cheques etc.

---

