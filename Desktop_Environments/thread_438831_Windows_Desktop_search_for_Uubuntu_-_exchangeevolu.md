---
title: "Windows Desktop search for Uubuntu - exchange/evolution"
date: 2007-05-10
forum: Desktop Environments
---

### Post by thikrat on 2007-05-10
Hello All,

I have been voraciously reading the posts in the ubuntu forums regarding Evolution, Exchange, the data connector and about indexing and metadata tools Tracker and Beagle.

My issue is this,  from reading the posts, I have learned that Evolution accesses exchange via WebDAV and is basically acting as a front end to the OWA interface.  This is the reason it is slow, is due to the fact that it cannot speak natively with exchange and must go the web route.

I also learned of a project called Brutus which looks to fix this, but I cannot use it because it requires the install of software on the windows server itself (the brutus server portion).
While evolution does in fact work, it is extremely slow.

That is issue #1... issue #2 is..

I cannot completely index my e-mails with Beagle, beagle seems to only index e-mails that were sent or received (NEW) inside evolution.  Not only that, it seems to only index the subject/sender/receiver and not the body of the message.  

I am stuck on windows because of exchange and windows desktop search.  The desktop search indexes all exchange e-mails, even archives.  totally and completely.  Is there any way for me to get past this or am i completely stuck?  I have been looking for about 10 days now.

#3...

If problem #2 can be solved then #1 is not as big a deal, BUT this is heavily related to #2.  I have an archive of old outlook mail that is 5 years old.  I want to import this to evolution and have it indexed so its searchable by Beagle.

Is Beagle the issue here?  (should I try tracker?) or is evolution the culprit?

both maybe?

---

### Post by dbera on 2007-05-10
You might get some authoratitive answer by asking this on the beagle mailing list. From what I know, "beagle seems to only index e-mails that were sent or received (NEW) inside evolution. Not only that, it seems to only index the subject/sender/receiver and not the body of the message" is because of a particular way that evolution is working.

---

