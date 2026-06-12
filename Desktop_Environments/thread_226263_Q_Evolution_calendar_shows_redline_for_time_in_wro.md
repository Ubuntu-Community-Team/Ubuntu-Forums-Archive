---
title: "Q: Evolution calendar shows redline for time in wrong place"
date: 2006-07-31
forum: Desktop Environments
---

### Post by Zlatan on 2006-07-31
e.g., when I have 10:14, redline in evolution calendar is at 9:14
how could I fix it?

thank you.

---

### Post by elamericano on 2007-03-15
This happened to me too. Evolution uses it's own time data, and a new package was not made for Dapper.

My time data is located at: /usr/share/evolution-data-server-1.6/zoneinfo/America/Los_Angeles.ics, but your city may be different. Looking at the file, there are two lines which describe the start of Standard Time and the start of Daylight time:
```
RRULE:FREQ=YEARLY;BYMONTH=10;BYDAY=-1SU
RRULE:FREQ=YEARLY;BYMONTH=4;BYDAY=1SU
```
This reflects the old rules of "Standard" starting on the first Sunday of the 4th month and "Daylight" starting on the last Sunday of the 10th month. Changing to the second Sunday in March and the first Sunday in November gives us:
```
RRULE:FREQ=YEARLY;BYMONTH=11;BYDAY=1SU
RRULE:FREQ=YEARLY;BYMONTH=3;BYDAY=2SU
```
Don't move the lines or change anything other than the number of the month and the Sunday (Daylight start went from negative to positive - last Sunday to first Sunday)

Exit and restart Evolution, and there you have it!

---

### Post by elamericano on 2007-03-15
Oops, I just noticed that you couldn't possibly be talking about the 2007 US DST change. Sorry, nevermind :) 
You probably just had your Evolution timezone set wrong, since it is set separately than system timezone. Go to Edit->Preferences.

---

