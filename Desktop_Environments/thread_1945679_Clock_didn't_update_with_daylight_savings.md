---
title: "Clock didn't update with daylight savings"
date: 2012-03-23
forum: Desktop Environments
---

### Post by GregoryMA on 2012-03-23
Hello, I live in Haiti and this year for the first time Haiti has daylight savings time.  But my clock didn't change when daylight savings came into effect a week or two ago.  I am guessing that whatever system the Ubuntu clock ties into to automatically change time doesn't realize that Haiti is on daylight savings or if it does it is not updated.  Either way my clock is an hour off.

I am looking for a way to fix it.  I tried to change the time by switching it to "Set the Time Manually".  But I can't get it to stay on the time I set it.  I always goes to some crazy time like 7:00 in 1969 when I hit enter.

If anyone could help me fix this, either by making the automatically updated clock work with daylight savings or helping me use the manual clock it would be great.  

Thanks, Greg

---

### Post by caco on 2012-03-23
Did you specify the full date string when setting time from the console? sudo date -s "2012-03-23 18:04:50"

Have you tried setting your system time and date from the hardware, if you are having problems.

---

### Post by Frogs Hair on 2012-03-23
7:00 pm  in 24hr format is 19:00 , so if setting manually choose the 12hr format if that is what you are used to. I don't know if the daylight savings time change is a function of Ubuntu software or if the sever needs to be changed to reflect daylight savings time in Haiti .

---

### Post by beanhead on 2012-03-23
you may want to update your time with a somewhat local time server see if you can find the ntp server ;coal to you. use that in your clocks advanced tab. That should help, your government must run time servers there. They MUST reflect the new day light saving time.

---

### Post by Bobhuber on 2012-03-23
Its a function of Ubuntu. Make sure your system updates are current.No clue about what servers you use or how they manage that sort of thing. I happened to notice the update because I don't have my system setup to update unless I request it.

---

### Post by GregoryMA on 2012-03-27
Thanks for all the feedback.  Just now I changed my location to a city with the right time (Dallas).  It will work for now.  If the 12.04 doesn't fix this I will have to actually fix it properly.

---

