---
title: "[SOLVED] Evolution Exchange Calendar not working after upgrade"
date: 2008-05-30
forum: Desktop Environments
---

### Post by tytus on 2008-05-30
I upgraded evolution last night from 2.22.1-0ubuntu3.1 to 2.22.1.1-0ubuntu3 and the exchange calendar stopped working completely. When I click on the calendar icon I get a dialog box asking for password. After typing the password I am getting the following error:

```
Error on exchange://myusername;auth=Basic@server.mycompany.com/:
 Authentication failed
```Alternatively sometimes I get another error:
```
The Evolution calendar has quit unexpectedly.
Your calendars will not be available until Evolution is restarted.
```Has anybody seen it or this is just me?

Any help in solving this greatly appreciated.

---

### Post by tytus on 2008-05-30
> **tytus said:**
> 
```
The Evolution calendar has quit unexpectedly.
Your calendars will not be available until Evolution is restarted.
```Has anybody seen it or this is just me?


I started evolution with --debug flag here are the debugs corresponding the the above error:

```
(evolution:11854): libecal-WARNING **: e-cal.c:318: Unexpected response
calendar-gui-Message: Check if default client matches (1211469647.14443.0@spinaker 1212155574.7796.3@spinaker)

(evolution:11854): calendar-gui-CRITICAL **: e_week_view_add_event: assertion `end > add_event_data->week_view->day_starts[0]' failed

(evolution:11854): calendar-gui-CRITICAL **: e_week_view_add_event: assertion `end > add_event_data->week_view->day_starts[0]' failed

(evolution:11854): calendar-gui-CRITICAL **: e_week_view_add_event: assertion `end > add_event_data->week_view->day_starts[0]' failed

(evolution:11854): calendar-gui-CRITICAL **: e_week_view_add_event: assertion `end > add_event_data->week_view->day_starts[0]' failed

(evolution:11854): calendar-gui-CRITICAL **: e_week_view_add_event: assertion `end > add_event_data->week_view->day_starts[0]' failed

(evolution:11854): calendar-gui-CRITICAL **: e_week_view_add_event: assertion `end > add_event_data->week_view->day_starts[0]' failed

```I also tried deleting the exchange account and re-adding it again but this does not fix anything.

---

### Post by tytus on 2008-06-03
OK. The problem was fixed by installing pre-released version of evolution update. Here are the packages that were upgraded on my system when I enabled pre-release updates and checked in evolution check box:
```
Upgraded the following packages:
evolution (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-common (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-data-server (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-data-server-common (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
evolution-exchange (2.22.1-0ubuntu1) to 2.22.2-0ubuntu1
evolution-plugins (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libcamel1.2-11 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libebook1.2-9 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libecal1.2-7 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedata-book1.2-2 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedata-cal1.2-6 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libedataserver1.2-9 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libegroupwise1.2-13 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libgdata-google1.2-1 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1
libgdata1.2-1 (2.22.1.1-0ubuntu3) to 2.22.2-0ubuntu1

```There is also a discussion about it on evolution mailing list under subject: "Evo started asking for Keyring password every time I start Evo"

---

