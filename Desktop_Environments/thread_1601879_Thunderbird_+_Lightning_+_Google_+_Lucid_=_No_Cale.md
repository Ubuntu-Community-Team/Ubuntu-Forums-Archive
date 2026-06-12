---
title: "Thunderbird + Lightning + Google + Lucid = No Calendar"
date: 2010-10-20
forum: Desktop Environments
---

### Post by klausner on 2010-10-20
I have TBird 3.1, Lightning 1.02b, Provider for Google Calendar 0.71 installed on lucid. Mail works fine. I entered the XML for the gcal location, but I see no calendar events.

Tried deleting and re-creating the entry. No change.

Why doesn't the data from the Google calendar load? Clicking on *Reload Remote Calendars* has no effect.

---

### Post by astrobob.tk on 2011-01-22
> **klausner said:**
> I have TBird 3.1, Lightning 1.02b, Provider for Google Calendar 0.71 installed on lucid. Mail works fine. I entered the XML for the gcal location, but I see no calendar events.

Tried deleting and re-creating the entry. No change.

Why doesn't the data from the Google calendar load? Clicking on *Reload Remote Calendars* has no effect.


Are you using the public or private xml ?
try the private one as it gives read/write access.

hope this helps

---

### Post by gaellafond on 2011-08-24
Same problem here.

I'm using the right XML, I can see all events when I visit the URL using Firefox. Some events are missing in Thunderbird (the last one to be exact). When I reload the calendar using "Right click on the calendar" > "Reload remote calendars", nothing append. Even restarting Thunderbird itself do not help.

I'm using Ubuntu Maverick

---

### Post by gaellafond on 2011-08-24
I think I have an explanation.

The only event that do not show up in my calendar has the following entry in the XML file:
Replaces event originally scheduled for: ...

This is the only event with this entry. I think Thunderbird do not handle rescheduling very well. I fixed my problem by accepting the event and making a duplication of it using the Web interface on the Calendar in GMail.

---

