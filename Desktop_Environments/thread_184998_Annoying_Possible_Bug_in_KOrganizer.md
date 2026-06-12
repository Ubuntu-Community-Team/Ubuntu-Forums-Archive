---
title: "Annoying Possible Bug in KOrganizer"
date: 2006-05-30
forum: Desktop Environments
---

### Post by hermesrules on 2006-05-30
As of recently, I've been experiencing something really annoying when I use Kontact, and KOrganizer in particular. For a while, I wasn't sure what was going on. Every time I start Kontact (it starts in KMail by default), and then try to switch to Calendar (KOrganizer), Kontact seems to hang, and I have to kill it. I tried running KOrganizer from the console, and as soon as it starts up, it spews countless error messages, which look like these:

```
/build/buildd/kdepim-3.5.2/./libkcal/libical/src/libical/icaltime.c:147: icaltime_from_timet() is DEPRECATED, use icaltime_from_timet_with_zone() instead
```

I see this scrolling up my screen or a few seconds (possible a few hundred lines of the same message), and once it's gone, this is what comes next:

```
QGArray::at: Absolute index 1052 out of range
```

The number goes well into the thousands by an increment of 4. At this point, I can only use Ctrl+C to stop it, and KOrganizers stops.

I suspect the exact same things happens when I try to use some of the other components. Interestingly, I did remove --purge on KOrganizer, and then reinstalled it. It ran fine the first time after the reinstallation, and and exhibited the same behavior the next time I started it. This is extremely annoying, as I can't use my calendars, or my contacts, or anything other than mail.

Has anyone encountered anything like this? I think it might have to do with adding Gmail calendar to Kontact using the ical link. Funnily enough, it used to work for at least a few days - I have GMail, the local calendar, and a Calendar on an Exchange server displayed together in KOrganizer.

Does anyone have any suggestions, and what do you think - is it likely this is a bug, or is it just some screwed up config file on my computer? Any help is greatly appreciated.

Thanks.

---

### Post by hermesrules on 2006-05-31
In less than 12 hours, this post got burried under 8 pages of threads! Wow, I love these forums! But, still, anyone out there who has any idea why I have this problem?

---

### Post by Hezekiah on 2006-05-31
I'm not sure, but have you submitted a bug report and/or checked to see if there is an existing bug report describing the same problem?  It sounds like a pretty serious issue, so it's probably worth submitting.

---

### Post by hermesrules on 2006-05-31
[QUOTE=Hezekiah]I'm not sure, but have you submitted a bug report and/or checked to see if there is an existing bug report describing the same problem?  It sounds like a pretty serious issue, so it's probably worth submitting.[/QUOTE]

Thanks for your suggestion. I did what I could, and submitted a bug at Launchpad.net, number 47708. Unfortunately, I have no way of following the instructions on how to file a bug, and hope that it would still be helpful to the developers.

Anyone else with similar issues? Those of you who have GMail Calendar enabled in KOrganizer, does it work fine?

---

### Post by Hezekiah on 2006-05-31
For what it's worth, I've submitted several bugs without going through the full process they describe, and most of them have been fixed - while submitting without all of the extra details may not be ideal, it's not always feasible to do everything they ask for.

---

### Post by hermesrules on 2006-06-01
I just tried to run Kontact as root (via kdesu), and that problem is not present. Could it be something with my user profile then? How do I reset it? Even if it is the profile, this can still be a bug as it just happens without any warning...

---

