---
title: "evolution google contacts sync problem"
date: 2010-08-17
forum: Desktop Environments
---

### Post by BarryDocks on 2010-08-17
Currently running 10.04 32bit edition with evolution installed.  Have successfully managed to sync gmail account and google calender but having trouble with the contacts list.  Contacts added to google will appear in the contacts list in evolution but a contact added via evolution results in a n error - "Error Adding Contact - other error" helpful!  Nothing in the syslog.

After a google around, I found reference to the need to specify google public DNS servers but this has not helped.

Suggestions would be great!  Thanks

---

### Post by BarryDocks on 2010-09-23
Bump

Anyone?

---

### Post by mattgreen on 2010-09-24
Hi, I'm using Ubuntu 10.04 32bit with Evolution 2.28.3.

I'm having trouble synchronising with my Google contacts - I get the following message:-


"The Evolution address book has quit unexpectedly.

Your contacts for google://<my email address> will not be available until Evolution is restarted."

Needless to say, I restart it an it doesn't behave any differently. I've even tried adding a new Google account to no avail.

I'll check the launchpad bug reports...

Matt

---

### Post by mattgreen on 2010-09-27
Further to this I have managed to get it to work...

My Google account has two usernames (I think this might be common), one of them is a username I used for Google services **before** I had a GMail account and the second is effectively my GMail address.

I was trying to authenticate (via Evolution) using the older, alternative username. Once I switched over to use the newer username all seems to work fine.

So I guess the API that the Evolution Google plugin uses to talk to Google doesn't support authentication using the alternative username.

Hope that helps?

---

### Post by BarryDocks on 2010-09-30
No, I can't get it to work with a brand new google account.  Same problem everytime

---

