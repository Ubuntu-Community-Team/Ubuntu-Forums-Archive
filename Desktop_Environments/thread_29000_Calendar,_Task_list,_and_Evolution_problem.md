---
title: "Calendar, Task list, and Evolution problem"
date: 2005-04-22
forum: Desktop Environments
---

### Post by mattack on 2005-04-22
I use the task list in Evolution, a lot. I like to look at it by clicking on the clock in my Gnome Panel... However, recently tasks that I have checked off still show up there when I click on the time... To get them to completely disappear, I have to delete the entry in Evolution. This is annoying to have to open up Evolution to check off a completed task, especially if I check it off from the panel, it doesn't appear in Evolution.
I want to be able to check off tasks in either place, Evolution and from the panel's calendar/clock, and have them not display in either place...
How can I do this?

see attached screenshot for clarification

---

### Post by Bob D. on 2005-04-22
I agree with you, that should be how the applet works. It should inherited the setting from Evolution. However, this appears to be a shortcoming of the Clock Applet. I'd suggest filing a feature enhancement bug at the Gnome [Bugzilla]("http://bugzilla.gnome.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&field0-0-0=product&type0-0-0=substring&value0-0-0=clock&field0-0-1=component&type0-0-1=substring&value0-0-1=clock&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=clock&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=clock&field1-0-0=product&type1-0-0=substring&value1-0-0=applet&field1-0-1=component&type1-0-1=substring&value1-0-1=applet&field1-0-2=short_desc&type1-0-2=substring&value1-0-2=applet&field1-0-3=status_whiteboard&type1-0-3=substring&value1-0-3=applet").
 
Bob

---

### Post by mattack on 2005-04-22
[QUOTE=Bob D.]I agree with you, that should be how the applet works. It should inherited the setting from Evolution. However, this appears to be a shortcoming of the Clock Applet. I'd suggest filing a feature enhancement bug at the Gnome [Bugzilla]("http://bugzilla.gnome.org/buglist.cgi?bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&field0-0-0=product&type0-0-0=substring&value0-0-0=clock&field0-0-1=component&type0-0-1=substring&value0-0-1=clock&field0-0-2=short_desc&type0-0-2=substring&value0-0-2=clock&field0-0-3=status_whiteboard&type0-0-3=substring&value0-0-3=clock&field1-0-0=product&type1-0-0=substring&value1-0-0=applet&field1-0-1=component&type1-0-1=substring&value1-0-1=applet&field1-0-2=short_desc&type1-0-2=substring&value1-0-2=applet&field1-0-3=status_whiteboard&type1-0-3=substring&value1-0-3=applet").
 
Bob[/QUOTE]

It used to act correctly back in Warty... then I installed something (upgrades or new software, I forget which), and it started acting goofy.

I've looked at Bugzilla before, It just confuses me mostly...

---

### Post by Bob D. on 2005-04-22
Hmmm, I was never able to get it to work as we've discussed.

I filed a bug here: [http://bugzilla.gnome.org/show_bug.cgi?id=301648]("http://bugzilla.gnome.org/show_bug.cgi?id=301648").Bug filing really isn't that hard, though I agree that Bugzilla isn't the most user friendly place.

Bob

---

### Post by mattack on 2005-04-22
Thanks for filing the bug. It looks okay to me.
Funny thing is my checked off tasks are now not showing in the applet. I checked in Evolution and unchecked the "hide completed tasks" box and they showed up in Evolution...  weird.

---

