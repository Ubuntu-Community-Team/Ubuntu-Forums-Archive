---
title: "clock widgets showing wrong time after daylight saving change"
date: 2018-11-27
forum: Desktop Environments
---

### Post by danny44 on 2018-11-27
kubuntu 18.04
KDE plasma 5.12.7


my timezone changed from summer time to standard time recently. Ever since all the clock widgets are wrong - digital clock is 2 hours behind. Analogue clock and fuzzy clock are 2 hours ahead.


Date & time in system settings shows the right time and is set to use automatic date and time. Timezone is set to my current time zone. Running 'date' in command line shows the correct time and timezone


Digital clock widget has an option to configure timezone. Setting to my system time and and my actual timezone doesn't fix it. 


Analogue clock and fuzzy clock have no time or timezone configuration so I presume they are meant to be tied to the system time.

---

### Post by T.J. on 2018-11-28
> **danny44 said:**
> kubuntu 18.04
KDE plasma 5.12.7


my timezone changed from summer time to standard time recently. Ever since all the clock widgets are wrong - digital clock is 2 hours behind. Analogue clock and fuzzy clock are 2 hours ahead.


Date & time in system settings shows the right time and is set to use automatic date and time. Timezone is set to my current time zone. Running 'date' in command line shows the correct time and timezone


Digital clock widget has an option to configure timezone. Setting to my system time and and my actual timezone doesn't fix it. 


Analogue clock and fuzzy clock have no time or timezone configuration so I presume they are meant to be tied to the system time.

Do you have Windows installed on your computer as well?

---

### Post by danny44 on 2018-11-28
> **T.J. said:**
> Do you have Windows installed on your computer as well?

no

---

### Post by T.J. on 2018-11-28
Interesting.  

Do you have local or UTC set in your /etc/adjtime?  Have you checked your battery?

---

### Post by danny44 on 2019-01-03
> **T.J. said:**
> Interesting.  

Do you have local or UTC set in your /etc/adjtime?  Have you checked your battery?

/etc/adjtime doesn't exist on my system

not a battery issue as Date & time in system settings and 'date' in command line shows the correct time and timezone

---

