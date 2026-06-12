---
title: "first day of week"
date: 2005-10-30
forum: Desktop Environments
---

### Post by mpalczew on 2005-10-30
somehow after upgrading to breezy the day of the week in the bottom right starts on Monday instead of Sunday does anyone know how to change it.

I know that many people think it's more logical to have it start with monday, but everyone else here thinks it starts on sunday, therefore this calendar is totally out of sync with the rest of the countries calendars.

---

### Post by mpalczew on 2005-10-30
sorry I should have been more specific the clock applet has a calendar that pops up when you click on it.   it is this calendar that starts on monday instead of sunday

---

### Post by i0h on 2005-10-30
what are you talking about?...  my calander in the clock (upper right) is starting with monday.. and monday is the normal day to start with :)

---

### Post by gaboro on 2005-11-01
[QUOTE=i0h]what are you talking about?...  my calander in the clock (upper right) is starting with monday.. and monday is the normal day to start with :)[/QUOTE]
it should depend on locale, but it is just weird: for Hungary, it should be Monday, but it is Sunday at my desk. 
moreover, appointments (e.g. date of birth) from the evolution calender will be displayed, which is a nice feature, but the text is truncated... Wrong control used i guess...

cheers
gaboro

---

### Post by gjaffe on 2005-11-01
[QUOTE=mpalczew]somehow after upgrading to breezy the day of the week in the bottom right starts on Monday instead of Sunday does anyone know how to change it.[/QUOTE]

Same thing happened to me.  This affects jpilot and even a home brew pygtk script I wrote.

I've tried just about everything after reading lots of stuff on the Internet.  All I managed to do was to mess up my locales package enough so that I had to do a reinstall of it.  :confused: 

Anyone have a clue on how to fix this?

---

### Post by Hairy_Palms on 2005-11-01
ive got the exact opposite problem, mine starts on sunday but i would like it to start on monday, not a big deal just a small irritation.

---

### Post by Buffalo Soldier on 2005-11-01
Try checking the settings in Evolution. Go to Edit -> Preferences -> Calendar & Task -> Week Starts. I think the settings in Evolution controls the time/date applet.

---

### Post by gaboro on 2005-11-01
[QUOTE=Buffalo Soldier]Try checking the settings in Evolution. Go to Edit -> Preferences -> Calendar & Task -> Week Starts. I think the settings in Evolution controls the time/date applet.[/QUOTE]
evo is set to use monday, and it does so. clock applet undependently shows sunday in the first column. 
got no idea
cheers
gaboro

---

### Post by l33tc0d34 on 2005-11-01
i thought sunday was the 1st day of teh week.

---

### Post by gaboro on 2005-11-02
[QUOTE=l33tc0d34]i thought sunday was the 1st day of teh week.[/QUOTE]
at mpalczew's desk. however, he has monday instead. 
i'd like to see monday, however, i've got sunday. 
it depends on the country your live in.
cheers
gaboro

---

### Post by PhilOSparta on 2005-11-04
It appears that a bug has been submitted for this problem.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=16168](http://bugzilla.ubuntu.com/show_bug.cgi?id=16168)

Actually, I added 
first_weekday 7
first_workday 7

just after the LC_TIME-flag in the locales. Then run

locale-gen and reboot.
It worked for me.

---

