---
title: "Traveling, with laptop; Why won't Gnome panel clock show local time??"
date: 2010-09-30
forum: Desktop Environments
---

### Post by cpbl on 2010-09-30
Hello. When I travel, I would like to tell my laptop that I, as a user, am in a different time zone that what the OS may think is local. And I would like the clock on my desktop (default Gnome bar date/time display) to show the local time.

Instead, I currently have to use sudo and change the system time... (click on the clock, choose time settings, set system time -- there are no other choices given). The applet thing allows me to add other locations, but they only show up if I click on the icon, as extra times below the main one.

Am I missing something? Using the wrong app?

Thanks!

---

### Post by sendblink23 on 2010-10-01
I've never tried changing my clock.. but can you try this to see if it works for you?

First after getting the current location time

Then do..
Right-Click the Calendar in the Top
Preferences
Time Settings
Change the *Time -Hours/Min*(to the current location time)
then Click "Set System Time"

no clue if it works.. give it a try

---

### Post by sikander3786 on 2010-10-01
Under System > Administration > Time and Date, deselect "Keep synchronized with servers" and select "Manual". Change the settings, reboot and see if the settings persist.

Changes in Time and Date from Calendar last only until you reboot. You need root previledges to save it system wide.

---

### Post by cpbl on 2010-10-04
Thanks for these ideas.  Unfortunately, they are too far from what I want, and think is reasonable service.

I want to keep my clock synchronized with NTP.
I don't want the system time to change (which would mess up all kinds of security, file system checks, etc).
I don't want to have to manually fiddle with the clock (which would seem a strange and crude way to shift hours to a known zone).
My system clock is in UT. The way I understood it, my user interface (not the system) currently knows a time zone for me. Since the clock is in UT, it is always translated when displayed to show something rendered in my time zone. I would simply like to tell it that my time zone has changed, or better yet, that it has changed temporarily.

I suspect my picture of how things work must be wrong, in order to make my expected behaviour/feature difficult???

---

### Post by madhi19 on 2010-10-05
There a Firefox add-on call Foxclocks that give the time in all sort of time zone. Actually it customizable so that any time zone can be used. It not a fix for your problem but since most peoples spend almost 90% of their desktop time with a browser page open...

---

### Post by Zenmij on 2010-10-05
-

---

### Post by Zenmij on 2010-10-05
> **cpbl said:**
> Thanks for these ideas.  Unfortunately, they are too far from what I want, and think is reasonable service.

I want to keep my clock synchronized with NTP.
I don't want the system time to change (which would mess up all kinds of security, file system checks, etc).
I don't want to have to manually fiddle with the clock (which would seem a strange and crude way to shift hours to a known zone).
My system clock is in UT. The way I understood it, my user interface (not the system) currently knows a time zone for me. Since the clock is in UT, it is always translated when displayed to show something rendered in my time zone. I would simply like to tell it that my time zone has changed, or better yet, that it has changed temporarily.

I suspect my picture of how things work must be wrong, in order to make my expected behaviour/feature difficult???

I would respectfully suggest you're correct, there is a better method of going about what you're trying to achieve.

HOWEVER, off the top of my head - the button 'Set', when you hover over the multiple time zones SHOULD make it default for your gnome panel clock thingy - give it a minute.

Sorry if this is not what you're looking for.

---

### Post by cpbl on 2010-10-08
Zenmij, I'd like to try your advice, but I don't follow. How do you get to the multiple time zones / "set" option you speak of?

---

### Post by Zenmij on 2010-10-08
> **cpbl said:**
> Zenmij, I'd like to try your advice, but I don't follow. How do you get to the multiple time zones / "set" option you speak of?

On my Gnome Panel, when I click the time/date, I get a drop down menu.

Under the calendar is  "Locations" - clicking the arrow next to that gives me options to add different time zones that I wish to monitor. Then, by clicking the "Set" button, I can make it my default "Home" until I change time zones.

I'm not sure if that helps.

---

### Post by cpbl on 2010-10-26
> **Zenmij said:**
> On my Gnome Panel, when I click the time/date, I get a drop down menu.

Under the calendar is  "Locations" - clicking the arrow next to that gives me options to add different time zones that I wish to monitor. Then, by clicking the "Set" button, I can make it my default "Home" until I change time zones.

I'm not sure if that helps.

It certainly does!! That's perfect. The interface is actually lovely, does exactly what I thought it ought but couldn't figure out. (I guess maybe "set" should say "make local" or "set default" or something, to have made it more obvoius).

Zenmij, thanks very much for your reply and tutorial
c

p.s. Wow, now it even shows the local weather. before I had created a location, it did not, even though the default/main location was here...

---

### Post by pharbar on 2010-11-12
An N.B. regarding panel clock, local timezones and emails:

I knew about this ability to change the local time, but never implemented it for fear of messing up my email dates & times (in Thunderbird).

In case anyone wants reassurance, in Thunderbird (and other email clients?) the arrival time & date of emails is indeed displayed according to the computer's local time. However, this is UPDATED to reflect any subsequent changes to the local time, so the _order of emails is preserved_.

That is more sophisticated behaviour than I had suspected and pretty useful! Just wish I had tested that out before.

---

