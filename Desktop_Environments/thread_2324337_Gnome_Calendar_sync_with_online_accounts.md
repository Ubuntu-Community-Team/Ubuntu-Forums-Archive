---
title: "Gnome Calendar sync with online accounts"
date: 2016-05-12
forum: Desktop Environments
---

### Post by Zibi_Braniecki on 2016-05-12
I recently switched to Ubuntu + Gnome and I'm really happy with the setup. I'm on Dell XPS 13, Ubuntu 16.04, Wayland, with Gnome 3.20, most things works really well.

One things that I couldn't get working is syncing the calendar with online accounts. I have OwnCloud and Google Account, and when I open Calendar, select "Calendar Settings", I have an option to add online accounts, and when I add Google or OwnCloud I can see them in Nautilus (so I can access the files), and I can see contacts from Google in the Contacts app, so I know it's syncing.

But none of the online calendars shows as an option in "Calendar Settings" menu. I watched a youtube video with the demo of how it's supposed to work, and in the demo right after the account has been added it shower up in Calendar Settings below "personal" and "birthdays and anniversaries".

I don't even know how to debug this because it doesn't show any error and it looks like it should be working, except that it doesn't.

Anyone else with this problem? Any idea how can I debug this?

---

### Post by j_anthony on 2016-06-21
I had a similar problem, and I suspect the solution I found may help you, although I am running Gnome 3.18, one version earlier.

 I tried adding a couple of Caldav calendars from within the Calendar app; the setup proceeded with no errors and the calendars showed up in the calendar list, but none of the events were displayed and adding new events to the online calendars was disabled. Worse yet, deleting the broken calendars from within the Calendar app caused them to temporarily disappear from the list, but they would hang around and reappear later, still unusable.

Eventually I found [this article]("https://www.slightfuture.com/technote/gnome-caldav"), which suggests that adding online calendars from the Calendar app is broken and you should set them up in Evolution instead. Since all the Gnome calendar apps connect to the same backend, calendars set up from within Evolution are visible in the Calendar app as well.

When I opened Evolution, the broken calendars I had set up from within the Calendar app were listed. I deleted them in Evolution, closed the Calendar and Evolution apps, restarted Evolution, and set the online calendars up from scratch in Evolution. It worked like a charm, all events were displayed correctly, and now the calendars appear and work as expected in Gnome Calendar.

Since the calendars are stored in evolution-data-server, which is separate from Evolution, you don't need to mess with Evolution after the initial setup; you can even uninstall it without ill effects; I checked.

---

### Post by pierre-chabirand on 2017-02-03
Hi i had a similar problem. i added my gmail account in the parameters/online accounts (i am in 16.04). My google calendar did appear in california and agenda.
Hope this helps.

---

