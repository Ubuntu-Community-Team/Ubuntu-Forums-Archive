---
title: "Synchronizing and mapping Palm data to desktop applications (Evolution...)"
date: 2007-01-30
forum: Desktop Environments
---

### Post by snitgaard on 2007-01-30
Some time ago, I tried out synchronizing an older Palm (Palm Vx) with an Ubuntu installation. I encountered many of the problems described in the forums and did eventually abandon Ubuntu with regard to synchronization of my Palm. :(

Today, I have a more recent Palm (Palm Z22) and would really like make things work and possibly finally let go of Windows. And assuming that I manage to connect with my Palm, I would really like to see all my data witin Evolution using gnome-pilot. JPilot could be an option if it can handle a Palm OS5 device properly. Maybe just being able to backup my Palm could do.

I could imagine that syncing data into Evolution would be the best and most complete way of handling data in my Palm. To me, it seems that JPilot is limited to support the datastructures found in older Palm models like the Palm Vx.

Can someone share their experiences with synchronization of Palm devices (**Palm OS5**)? _Not_ the messing around with USB ports, pilot-link, gnome-pilot and stuff, but the actual mapping and transfer of data like contacts, calendar, memos, note pad and tasks. Any observations on various Ubuntu desktop applications would be nice.[INDENT] Is any information lost or changed in the synchronization process for **Contacts**? Could be various fields for contacts like **birthday**, **e-mail addresses**, **home **and **work addresses**, **spouse**, **photo**, etc.
[/INDENT][INDENT] How about the **Calendar**? **Recurring appointments**, **categories**, **birthdays linked to contacts**, **appointments spanning over multiple days**, **"all day" events**, **"no time" events**, **location**, etc.
[/INDENT][INDENT]**Tasks**? **Categories**, **priorities**, **due dates**, **repeating tasks**, etc.
[/INDENT][INDENT]**Memos**? Mapping them to **text files** in a folder is okay - categories as sub-folders could be okay.
[/INDENT][INDENT] Has anyone succeded in installing **Photos **to the Palm (to be viewed with the bundled **SplashData Photos**) - it seems to be possible to produce the photo PDB files using CLI ([http://www.pilot-link.org/blog/1324)]("http://www.pilot-link.org/blog/1324%29").
[/INDENT][INDENT] Any luck with AvantGo out there? What are my options here?
[/INDENT]Any other applications and well working conduits?

Thanks in advance for sharing...

---

### Post by cbrehm on 2007-02-01
I just installed Ubuntu on my home pc and I also have a Palm Z22 handheld that I want to sync with my Ubuntu. I saw a application in the menus that was called Palm OS but have not tried to sync it with evolution yet.

I will be trying this in the next few days and will post back here with the results.

---

### Post by snitgaard on 2007-06-06
So **cbrehm**, how are you doing by now? Have you tried out synchronizing you Palm Z22 with Ubuntu and **Evolution**?

I have done anything further within this area, but I guess that I can assign some time this summer to try it out. I am a bit puzzled about people reporting that they have made everything work with their (**OS5**) **Palm Tx**, **T5**, **E2**, **Zire**, **Z22**, etc. and **JPilot**. I simply don't under how this can be a workable solution, when e.g. address **information is missing in Contacts**, **categories in Tasks**, etc. Do you loose such information or is it only hidden? The article below gives some indications:

[howto-pages.org/palm_z22]("http://howto-pages.org/palm_z22/")

Please, share experiences.

---

### Post by reidi on 2007-08-12
I have a lot of the similar questions about field mapping.  I use ScheduleWorld to manage calendar and contacts, and syncevolution to get that information into Evolution.   Evolution calendar items seem to sync well with the PDA using gpilot.  But Evolution contacts are really a mess.  Most phone numbers are missing.  Email addresses often do not come across.  

In short: How does one make the Evolution address information come into the PDA correctly?

---

### Post by marcelo.matos on 2007-11-27
I know this tread is old, but I'm having the same problem with the contacts in Evolution.

There's a lot of different fields for contacts on palm software and the evolution counterpart. Maybe because of this, the sync is a mess and i lost a lot of information on the sync between my palm and PC.

For example, when I create a Contact on evolution with more than first and last name (3 names like John Nobody Doe), the middle name is not synced to Treo (only John Doe goes to the Treo, in the example I gave).

And when I create a contact on treo with various numbers (3 business numbers for instance), only one of then is synced to evolution.

Does anyone know a solution for syncing a Treo 650 in ubuntu with a trustworthy information transit?

Thanks,
Marcelo Matos

PS.: Sorry for my bad English.

---

