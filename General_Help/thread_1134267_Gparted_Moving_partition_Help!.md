---
title: "Gparted Moving partition Help!"
date: 2009-04-23
forum: General Help
---

### Post by ductiletoaster on 2009-04-23
Ok so i have a laptop that is currently running windows vista. i had it split into two partitions.... one for system files and the other for media. Well because of bad planning on my part i started running out of room on the "windows" partition and had a ton of room on my "media". So being a Ubuntu fan and user i knew about gparted and have used it extensivly But im having a problem.

laptops configuration:
sda1 "windows"
sda2 "media"

Gparted operations:
Shrink /dev/sda2 from to
Move /dev/sda2 to the right
Grow /dev/sda1 from 39.06gb to 58.07gb

My problem occurs with the second operation. I expected it to take a longtime cuz of the amount of data it had to move however its been two days now it appears as if the process has repeated several times. I checked it yesterday at about this 12:00pm and it was about an hour from finishing and then i went out of town and came back and it was 3 hours from finishing that same process. O forgot to mention that it also freezes very often though i have had that happen before and has never affected anything

WHAT DO I DO...? Thanks ahead of time

---

### Post by ivanvajar on 2009-04-23
This might have happened because drives are not defragmented (Windows drive).

---

### Post by ductiletoaster on 2009-04-23
I have done this on previous windows installs infact thats how i created the two partitions.... and usually fragmentation only effects the shrinking process not the moving. Damn microsoft and the fragmenting! how many OS's are out there that dont have this problem! Lol its to bad my GF needs windows other wise i would switch it to linux in a heartbeat

Thanks for the reply..... would you happen to know how to get it to finish this process. Or i had an idea... i know cancelling can have some major data loss but i noticed that this process is about 2 hours from finishing..... Knowing that it will just restart the second phase and not continue wouldit be best to cancel right when it "finishes" the second process before it starts it agian?

---

### Post by ductiletoaster on 2009-04-23
I also just remb that I pretty frequently defrag her laptop. and not with that crappy MS defrag.... i use one called jkdefrag and did it pretty recently.

---

### Post by meierfra. on 2009-04-23
> checked it yesterday at about this 12:00pm and it was about an hour from finishing and then i went out of town and came back and it was 3 hours from finishing that same process. O

That's normal. gparted does a practice (readonly) run, before it does the actual resizing. The "one hour" was the time until the end of the practice run.  The "3 hours" is  the time until the end of the resizing. After that gparted will do a filesytem check, which might take some time (but should be  faster than the  resizing)

> wouldit be best to cancel right when it "finishes" the second process before it starts it agian?
Don't cancel. gparted is   almost done.

---

### Post by ductiletoaster on 2009-04-23
Ok thank you lol.... im just not used to it taking so long. i have done this  before and it has never taken this long.... Must be the laptop!?

---

