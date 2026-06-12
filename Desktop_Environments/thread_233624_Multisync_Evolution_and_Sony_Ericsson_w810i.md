---
title: "Multisync Evolution and Sony Ericsson w810i"
date: 2006-08-10
forum: Desktop Environments
---

### Post by smolko on 2006-08-10
Hi,

I'm trying to synchronize my mobile phone (SE w810i) with evolution. It works fine only in one way, from the phone to computer. It can import my calendar, todo list and contacts.
When I run the synchronization from computer to phone. (it finds out, that there are new events to copy) I get a "Session failed" message on the phone. On the other hand Multisync seems confident with doing it's job faultlessly

```
[evo2-sync] DEBUG: start: sync_connect
[evo2-sync] INFORMATION: Loading state from file /home/smolko/.multisync/7/localsettings
[evo2-sync] DEBUG: end: load_palm_state
[evo2-sync] DEBUG: end: sync_connect
Found a new vevent
BEGIN:VCALENDAR
BEGIN:VEVENT
UID:20060809T084831Z-5533-1000-1-0@smolko-laptop
DTSTAMP:20060809T084831Z
DTSTART;TZID=/softwarestudio.org/Olson_20011030_5/Europe/Prague:
 20060812T133000
DTEND;TZID=/softwarestudio.org/Olson_20011030_5/Europe/Prague:
 20060813T120000
TRANSP:OPAQUE
SEQUENCE:4
SUMMARY:TEST_SUMMARY
LOCATION:TEST_LOCATION
CLASS:PRIVATE
CREATED:20060809T084844
LAST-MODIFIED:20060810T142433
DESCRIPTION:TEST_DESCRIPTION
END:VEVENT
END:VCALENDAR
tasks length msyncid7 0
[evo2-sync] INFORMATION: Done searching for changes. Found 1 changes
sync_done
```

Any help will be appreciated.

---

### Post by littleiffel on 2007-03-07
It's some time but maybe it helps you out:

[http://www.williambrownstreet.net/wordpress](http://www.williambrownstreet.net/wordpress)


I wrote everything related to sync and w810i

---

### Post by rwb on 2007-04-07
[COLOR="Blue"][SIZE="5"]**littleiffel **[/SIZE][/COLOR]

Great link :) I  have needed this for a while and struglled but now I'm one happy cup of coffee!!!

now all I need is some one to stop fiesty from failing to mount my SD card so  it works as it did with Kernel 2.6.20-12 not the loop it gets into with 2.6.20-14

---

### Post by duncansargeant on 2007-05-03
AHA!

I have the same one-way sync problem with my W800i.  I haven't solved it fully yet but narrowed it down to the wacky TZID in DTSTART and DTEND from evolution:

> 
```
DTSTAMP:20060809T084831Z
DTSTART;TZID=/softwarestudio.org/Olson_20011030_5/Europe/Prague:
 :
DTEND;TZID=/softwarestudio.org/Olson_20011030_5/Europe/Prague:
 20060813T120000

```


What I did to reproduce:

[LIST=1]
[*] create event in evo
[*] sync.  multisync says it syncs the entry, but it doesn't show up on the phone.
[*] right-click, save as, from evo, and save to a .ics.
[*] delete event from evo
[*] sync
[*] edit .ics, remove the TZIDs above so it says similar to just: DTSTART:20060812T133000 and the same for DTEND.
[*] import into evo
[*] sync
[*] tada - it appears on the phone.
[/LIST]

How to fix this properly?  I don't know.

---

### Post by duncansargeant on 2007-05-03
I tried this at home and to my surprise it worked.  Then I figured out the problem - its as simple as checking the "adjust for daylight savings" box in evolution.  Multisync log before and after:

```
Found a new vevent
BEGIN:VCALENDAR
BEGIN:VEVENT
UID:20070503T233853Z-3966-1000-1-3@viking1
DTSTAMP:20070503T233853Z
DTSTART;TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth:
 20070504T090000
DTEND;TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth:
 20070504T093000
SUMMARY:test 4
CREATED:20070503T233855
LAST-MODIFIED:20070503T233855
END:VEVENT
END:VCALENDAR
[evo2-sync] INFORMATION: Done searching for changes. Found 1 changes
Process: 0 1
List fullness: 0.076316 29 380
Got 1 changes.
Change type: 2, object type: 1
Comp: 
BEGIN:VCALENDAR
BEGIN:VEVENT
UID:20070503T233853Z-3966-1000-1-3@viking1
DTSTAMP:20070503T233853Z
DTSTART;TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth:
 20070504T090000
DTEND;TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth:
 20070504T093000
SUMMARY:test 4
CREATED:20070503T233855
LAST-MODIFIED:20070503T233855
END:VEVENT
END:VCALENDAR
Converted body:
BEGIN:VCALENDAR
BEGIN:VEVENT
UID:20070503T233853Z-3966-1000-1-3@viking1
DTSTAMP:20070503T233853Z
DTSTART:20070504T090000
DTEND:20070504T093000
SUMMARY:test 4
CREATED:20070503T233855
LAST-MODIFIED:20070503T233855
END:VEVENT
END:VCALENDAR

```

Notice the difference?  In the first one, DTSTART and DTEND have been mangled probably due to the non-standard TZID.  In the second one, it is converted perfectly to VCAL 1.0 and sent to the phone.

Yay.

---

### Post by duncansargeant on 2007-05-03
Sorry, I just realised they are both the "correct" version.  The following was what confuses multisync, which occurs when "adjust for daylight savings" is unchecked.

Note the TZ is ...Australia/Perth-(Standard).  Maybe the braces confuse multisync.

```

Changecounter: 110
New DBs: 0
Found a new vevent
BEGIN:VCALENDAR
BEGIN:VEVENT
UID:20070503T233754Z-3966-1000-1-2@viking1
DTSTAMP:20070503T233754Z
DTSTART;
 TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth-(Standard):
 20070504T093000
DTEND;
 TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth-(Standard):
 20070504T100000
SUMMARY:test 3
CREATED:20070503T233755
LAST-MODIFIED:20070503T233755
END:VEVENT
END:VCALENDAR
[evo2-sync] INFORMATION: Done searching for changes. Found 1 changes
Process: 0 1
List fullness: 0.073684 28 380
Got 1 changes.
Change type: 2, object type: 1
Comp: 
BEGIN:VCALENDAR
BEGIN:VEVENT
UID:20070503T233754Z-3966-1000-1-2@viking1
DTSTAMP:20070503T233754Z
DTSTART;
 TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth-(Standard):
 20070504T093000
DTEND;
 TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth-(Standard):
 20070504T100000
SUMMARY:test 3
CREATED:20070503T233755
LAST-MODIFIED:20070503T233755
END:VEVENT
END:VCALENDAR
Converted body:
BEGIN:VCALENDAR
BEGIN:VEVENT
UID:20070503T233754Z-3966-1000-1-2@viking1
DTSTAMP:20070503T233754Z
 TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth-(Standard):20070504T093000
 TZID=/softwarestudio.org/Olson_20011030_5/Australia/Perth-(Standard):20070504T100000
SUMMARY:test 3
CREATED:20070503T233755
LAST-MODIFIED:20070503T233755
END:VEVENT
END:VCALENDAR

```

---

