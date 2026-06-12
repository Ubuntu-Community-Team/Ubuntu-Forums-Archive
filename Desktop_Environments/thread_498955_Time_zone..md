---
title: "Time zone."
date: 2007-07-12
forum: Desktop Environments
---

### Post by DraconPern on 2007-07-12
I am curious why Ubuntu doesn't have standard time zone names like 'Central', or 'Eastern'.  Instead I get city names like  'America/Denver' when the list is clearly labeled 'timezone'.

What gives?

---

### Post by ewankho on 2007-07-12
Somebody correct me if I'm wrong, but I think 'central timezone' or 'eastern timezone' is only used in the US.

---

### Post by mtbsoft on 2007-07-12
Perhaps because Ubuntu is truly global and acknowledges that there is a world out there beyond the geographical limits of the united states.  

To me, living in Oz, Eastern standard time means GMT+11 (Sydney, etc.) and Western means GMT+8 (Perth) - "Central" is meaningless to me, whereas "America/Denver" at least gives me a clue.

---

### Post by DraconPern on 2007-07-13
> **mtbsoft said:**
> Perhaps because Ubuntu is truly global and acknowledges that there is a world out there beyond the geographical limits of the united states.  

To me, living in Oz, Eastern standard time means GMT+11 (Sydney, etc.) and Western means GMT+8 (Perth) - "Central" is meaningless to me, whereas "America/Denver" at least gives me a clue.

Please know your own country's timezones before trying to understand someone else's.  :)  You too have a CST.  [http://www.timeanddate.com/library/abbreviations/timezones/au/cst.html](http://www.timeanddate.com/library/abbreviations/timezones/au/cst.html)

Also, you said geographical limits. FYI, denver is a geographical location more so than a timezone which is why I am questioning what a geographic location is doing in a timezone list.

---

### Post by yabbadabbadont on 2007-07-13
Those timezones do exist.  Look in /usr/share/zoneinfo/US and you will see them.

```
/home/daffy $ cat /etc/timezone 
US/Central
```

---

