---
title: "Evolution Calendar and Task list not working"
date: 2008-01-10
forum: Desktop Environments
---

### Post by ThomasAagaardJensen on 2008-01-10
Suddenly my calendars and task list are no longer working properly.

- When I try to create an appointment (Ctrl+N) I get the message: "There is no calendar available for creating events and meetings". The calendar-file is in the filesystem though ($HOME/.evolution/calendar/local/system/calendar.ics).

- All my tasks are no longer displayed and I can't create new ones. The task-file is still in the filesystem (in $HOME/.evolution/tasks/local/system/tasks.ics).

- All appointments from my webcals don't show up.

All filepermissions seem okay, so what's wrong?

Evolution 2.12.1
Ubuntu 7.10 (with latest updates)

Thanks
Thomas

---

### Post by ThomasAagaardJensen on 2008-02-15
Solution found:
Do a backup followed by a restore!

Thomas

---

### Post by rh1zome on 2008-03-11
Yep, I've just had the same issue on with Evolution 2.12.1 on Ubuntu 7.10 with all current updates installed. Went to check my calendar this morning and nada! All calendar and memo data apparently missing. My most recent Evolution backup was at least two weeks old, and I didn't fancy losing my email for that period. Fortunately, the fix listed above worked for me. 

This glitch, or whatever causes this, is pretty alarming when it occurs!

---

### Post by andsongomes on 2008-04-24
I had same problems with evolution on Ubuntu 7.10, and I did a backup and restore. It's ok now. :)

---

