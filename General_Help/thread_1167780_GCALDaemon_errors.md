---
title: "GCALDaemon errors"
date: 2009-05-23
forum: General Help
---

### Post by jamesobooth on 2009-05-23
I'm running Ubuntu 8.10, Thunderbird 2, and am using GCALDaemon to sync my calendar up to my Google Calendar.  Recently I started getting some weird errors in my logs and GCALDaemon is failing to sync.

I've tried numerous things, even wiping my local calendar file and downloading a fresh copy from Google.  I also sync my calendar with GCALDaemon at work on a Windows machine which is having no problems.  This is specific to my Ubuntu machine.

Now, there are mentions of java in the errors.  I've installed java6 on both machines (Windoze and Linux) but when I run "java -version" on my Linux box I get the below:
java version "1.5.0"


GCALDaemon Errors below.  I've searched all over the web and am not getting anywhere.  Wondering if the gurus had any ideas.

2009-05-23 06:20:24 | FATAL | OnlineFileListener | Fatal service error!


  [1 ] net.fortuna.ical4j.data.ParserException: Error at line 359: Illegal WEEK_OF_YEAR.
   at net.fortuna.ical4j.data.CalendarParserImpl.parse(CalendarParserImpl.java:139)
   at net.fortuna.ical4j.data.CalendarBuilder.build(CalendarBuilder.java:167)
   at net.fortuna.ical4j.data.CalendarBuilder.build(CalendarBuilder.java:149)
   at net.fortuna.ical4j.data.CalendarBuilder.build(CalendarBuilder.java:137)
   at org.gcaldaemon.core.ICalUtilities.parseCalendar(ICalUtilities.java:155)
   at org.gcaldaemon.core.Synchronizer.syncronizeNow(Synchronizer.java:213)
   at org.gcaldaemon.core.Configurator.synchronizeNow(Configurator.java:1070)
   at org.gcaldaemon.core.file.OfflineFileListener.run(OfflineFileListener.java:61)
Caused by: java.lang.IllegalArgumentException: Illegal WEEK_OF_YEAR.
   at java.util.GregorianCalendar.nonLeniencyCheck(libgcj.so.90)
   at java.util.GregorianCalendar.computeTime(libgcj.so.90)
   at java.util.Calendar.setTimeZone(libgcj.so.90)
   at java.text.DateFormat.setTimeZone(libgcj.so.90)
   at net.fortuna.ical4j.model.DateTime.setTime(DateTime.java:202)
   at net.fortuna.ical4j.model.DateTime.<init>(DateTime.java:166)
   at net.fortuna.ical4j.model.property.DateProperty.setValue(DateProperty.java:140)
   at net.fortuna.ical4j.data.CalendarBuilder.propertyValue(CalendarBuilder.java:277)
   at net.fortuna.ical4j.data.CalendarParserImpl.parseProperty(CalendarParserImpl.java:236)
   at net.fortuna.ical4j.data.CalendarParserImpl.parsePropertyList(CalendarParserImpl.java:167)
   at net.fortuna.ical4j.data.CalendarParserImpl.parseComponent(CalendarParserImpl.java:334)
   at net.fortuna.ical4j.data.CalendarParserImpl.parsePropertyList(CalendarParserImpl.java:164)
   at net.fortuna.ical4j.data.CalendarParserImpl.parse(CalendarParserImpl.java:107)

---

### Post by jamesobooth on 2009-05-23
SOLVED

Tried the obvious and checked Google Calendar help.  Found the below:
[http://www.google.com/support/calendar/bin/answer.py?answer=99355](http://www.google.com/support/calendar/bin/answer.py?answer=99355)

Works like a charm!  \\

---

