---
title: "locale config trouble (and some solutions) (en_US)"
date: 2005-10-10
forum: Desktop Environments
---

### Post by jamesford on 2005-10-10
hi

ive been messing with /usr/share/i18n/locales/en_US in an attempt to change the time and date format + make monday first day in tray calendar (this because i want a 100% english system, but with norwegian time/date formats, including 24H time) 

now, the monday first thing ive got working using this as template [http://bugzilla.ubuntu.com/show_bug.cgi?id=16168](http://bugzilla.ubuntu.com/show_bug.cgi?id=16168)
(in short adding the following:
LC_TIME
first_weekday 1
first_workday 1
......)

the date i havent started on yet cos im still struggling with the 24H thing.  (yes i know u can choose 24H time going intot he trayclock preferences but that isnt system wide, for example the gdm screen still uses 12H am/pm)

ive managed to get rid of the AM/PM symbols by editing /usr/share/i18n/locales/en_US by replacing the am_pm and t_fmt_ampm with the following:
am_pm       "";""
t_fmt_ampm  ""

but HOW do i change it so that the system including gdm screen uses 24H time ? thats the big question

---

