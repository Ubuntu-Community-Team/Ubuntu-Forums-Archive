---
title: "Evolution doesn't connect to Google calendar"
date: 2011-08-09
forum: Desktop Environments
---

### Post by mcenno on 2011-08-09
Hello,


I'm failing to sync my evolution and Google calendars: during setup I get access to the list of Google calendars (evolution asks for password, and comes up with a list of my Google calendars), but after setup I get the following error:

Error loading calendar
Cannot open calendar: unexpected HTTP status code 3 returned

This is on a 64bit Natty system which I have upgraded recently from 10.04 to 10.10 and then to 11.04. 

Any ideas?


Thanks,

Enno

---

### Post by pilux59 on 2011-08-12
I can only tell you that you are not alone. Same thing happened to me. It worked initially on 11.04, but started failing about 3 days ago. I've tried recreating the account in Evolution, but without success so far.

---

### Post by lviggiani on 2011-08-22
Same happens to me... :(

Tried to google around but I couldn't find any solution...
Anyone?

---

### Post by lviggiani on 2011-08-22
Hi, I made some progresses on this:

My problem started when I set a proxy for internet connection. If I switch back to direct internet connection (without any proxy server) I can load my google calendar again.

BTW I have opened a [bug]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/830926") on launchpad to see what developers can do on this.

---

### Post by gpgp on 2011-08-30
Hi

I am having a similar problem. It looks like some guys over at the Arch linux forums kind of figured it out, but I do not have the same packages they do. See [https://bbs.archlinux.org/viewtopic.php?pid=983761]("https://bbs.archlinux.org/viewtopic.php?pid=983761")
I am not fluent enough to transcribe the problem to my package list but maybe someone else is ??

I am experiencing the same as one of the posters there, if I create a new google calendar in evolution, i can a see a list of my calendars to select so we know connectivity is there, but it will either never connect after being selected or return an html error code of 4 for me but others saw 3 and 5 as well. This is a recurring problem too as i have had evolution syncing with google calendars on and off for at least 2 years.

gpgp

---

### Post by nmyrick on 2011-09-17
Same issue here with Ubuntu Lucid Lynx.  I had Google calendar working with evolution, but a few weeks ago it just stopped syncing.  Now, when I try to create an appointment, I get an 'invalid object' error.

So I deleted my Google calendar in evolution, and tried to recreate it, and now I get the list of available calendars and it shows no error when creating the calendar, creates the calendar, but it never syncs.

---

### Post by nmyrick on 2011-09-17
I'm about to give up on Evolution for my calendar sync, since there are so many issues with it.  When I had a yahoo mail account, I could never get it to sync with Yahoo calendar, which is one of the reasons I switched to gmail.  Now this.

Does anyone know of a better calendar to sync for Ubuntu?  I don't want to have to open a web browser all the time to look at my calendar.

---

### Post by haqking on 2011-09-17
working fine for me in 10.10, no help to you but at least you know its working somewhere ;-)

---

