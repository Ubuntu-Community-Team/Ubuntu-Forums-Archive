---
title: "Evolution mishandles .ics files"
date: 2011-01-18
forum: Desktop Environments
---

### Post by jcoles on 2011-01-18
It should be possible to open a .ics file with Evolution in order to add the event it contains to the Calendar. 

It is possible to right-click the file and select Open with Evolution, but nothing happens. 

As an alternative, I tried importing the .ics file from within the Evolution calendar. Success! But, not quite:

In the calendar, the appointment appears on Thursday 20-Jan at 9pm, correct. But if you mouse-over the appointment, you see:

Time: Tomorrow 21:00 (1 hour)
   [Tomorrow 18:00 Daylight Savings Time]

Now we have uncertainty. Tomorrow is Wednesday not Thursday. And why are two times shown? 

Worse. I now right-click and open the event. The time shown inside is the 18:00 to 19:00 20-Jan, the second and incorrect time I saw in the calendar view. I correct the time to 21:00-22:00 and save. 

In the calendar, the event now appears at 00:00 Friday 21-Jan. Mouse-over shows this time, followed by "[Tomorrow 18:00 Daylight Savings Time]". I open the event and see the correct time of 21:00 - 22:00 20-Jan. 

The event now has three different times associated with it. If I request an alert, at which of the three times will it go off? 

Is there any sort of misconfiguration that could cause this bizarre behaviour? Or, is it simply an incompetent application?
My system is 64-bit Ubuntu 10.04, with Evolution 2.28.3.

---

