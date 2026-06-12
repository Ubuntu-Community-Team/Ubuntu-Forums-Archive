---
title: "Evolution calendar is mangling dates."
date: 2006-01-31
forum: Desktop Environments
---

### Post by brucebertrand on 2006-01-31
OK, I'm using Evolution to subscribe to a remote calendar ( .ics ) for viewing only.
The events in the remote calendar are being stored in UTC.  
Evolution is set to my local timezone (US Eastern time).  
Everything is displaying properly in Evolution.  An event that should happen at 5pm EST shows up as 5pm.

However, when I have an event that begins after 7pm EST (midnight UTC) AND repeats, the repeated dates show up as the correct time, but one day before they should.  The original date is fine.

For example, I have an event that happens on Wed, Feb 1 from 7:30 - 10pm.  It repeats every Wednesday through August.  The Feb. 1 date displays as it should, but the next occurrence shows up as Tue, Feb 7 from 7:30 - 10pm.  Every occurrence but the first one shows up as a day earlier.

When I change my timezone in Evo to UTC, everything shifts forward 5 hours as expected, but the 1 day displacement problem persists.

I've double checked the .ics file for proper formatting, and its fine.  When I subscribe to the same calendar in the Firefox calendar extension, everything displays properly.

Any ideas?
Thanks.

---

