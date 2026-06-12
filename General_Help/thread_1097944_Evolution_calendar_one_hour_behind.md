---
title: "Evolution calendar one hour behind"
date: 2009-03-16
forum: General Help
---

### Post by senor_smile on 2009-03-16
I just recently switched to using Evolution calendar.  I prefer it to Thunderbird.  It just seems more responsive and easier to work with to me.  I have a problem however.  For some reason, all alarms come through an hour late(e.g. I set an appt for 10am with a 5 minute alarm; that alarm comes through at 10:55 instead of 9:55).  Also, the red line showing what the current time is, is an hour behind.  I also have added a google calendar.  All appointments show up one hour behind where they should be.  Also, if I click the clock and expand appointments, all entries show one hour behind what they are entered as in evolution.  

--shaun

---

### Post by jonobr on 2009-03-16
what does typing the command date on the command line show?

Correct time or different to what you expect?

---

### Post by senor_smile on 2009-03-16
> **jonobr said:**
> what does typing the command date on the command line show?

Correct time or different to what you expect?


All other systems have the correct time, as far as I can tell.   

```
shaun@shaun-work-ubuntu:~$ date
Mon Mar 16 13:41:36 PDT 2009
```

Which is the correct time for the Pacific time zone.  

--shaun

---

### Post by jonobr on 2009-03-16
DOing some research on this, evolution seems to maintain its own timezone info and this issue was reported some time before

[This]("http://ubuntuforums.org/showthread.php?t=383560") link discusses a similar fix.
The launchpad shows mention of this in 2007, but I cant find later occurrences.

If you go to make changes as noted in the link, recommend you back up your file first.

---

### Post by senor_smile on 2009-03-16
SOLVED!
\
I have fixed it and it had nothing to do with that file.  Under
Edit, preferences, calendars and tasks
my time zone was set to Pacific/pitcaim.  I don't know where that is, but I found the American time zones called America.  So I selected America/Los angeles and all is well.  Thanks for the help.

---

### Post by jonobr on 2009-03-16
Excellent, recommend you marked as solved for people searching with similar problems

---

### Post by senor_smile on 2009-03-16
> **jonobr said:**
> Excellent, recommend you marked as solved for people searching with similar problems

Where can I change the thread's name to mark it as solved?

---

### Post by senor_smile on 2009-04-09
> **jonobr said:**
> Excellent, recommend you marked as solved for people searching with similar problems

How do I change the name of the thread to add [solved]???

---

### Post by leonardo_neo on 2009-04-09
> **senor_smile said:**
> How do I change the name of the thread to add [solved]???

This feature is disabled for some time past. 

It is recommended to 'tag' the question as 'solved', which other users can see.

Above the "quick reply" line, **right side** of the page, you will find edit tags option.

:)

---

### Post by Brian Vaughan on 2009-05-19
I just ran into this very same problem. I'm in the Pacific time zone, which is correctly set elsewhere, and yet in Evolution, I was listed as Pacific/Pitcairn.

Is this a matter of Evolution misinterpreting the system-wide time zone settings? If not, why doesn't it just read the time zone from the system settings?

---

