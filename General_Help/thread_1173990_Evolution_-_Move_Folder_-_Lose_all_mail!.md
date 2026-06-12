---
title: "Evolution - Move Folder - Lose all mail!"
date: 2009-05-30
forum: General Help
---

### Post by kubug on 2009-05-30
Hi all Evolution Experts,

here it is: I moved some folders, which contained emails that are filtered out (like emailed reports, ads, different accounts and such). I had them all under the Inbox Folder. But then they got too many, and I moved them down to the "On this Computer" *folder*. 

Everything worked great and I checked to see if all the emails moved and sure enough, everything was good. 

Closed the program and later on I started Evolution back up. It received some emails, and as soon as the filters moved an email into the new folders, it deleted all existing emails in the folder! What the ...


A.) How can I get my emails back?
B.) How can I prevent that in the future?

P.S.: This can be reproduced by having a mail filter move messages into a folder, then move the folder somewhere else, update the filter. As soon as another mail gets there, the old messages will be deleted.

---

### Post by Jesse Weinstein on 2009-09-14
This is a due to the index getting screwed up, according to [http://www.go-evolution.org/Camel.Local#Mbox_bugs]("http://www.go-evolution.org/Camel.Local#Mbox_bugs").  I found I could get my mail back by deleting the .ibex.index.data files and restarting Evolution.  I don't know what to do to keep it from happening again, though.

---

### Post by kubug on 2009-09-14
Awesome! Thank you. I got all my emails back even after all this time. Also, I am finally able to clear out the Trash folder (which before just gave me a nondescript error). 

If it happens again, I guess I will just look for this thread again.

Thanks again.

---

