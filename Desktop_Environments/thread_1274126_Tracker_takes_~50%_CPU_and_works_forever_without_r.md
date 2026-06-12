---
title: "Tracker takes ~50% CPU and works forever without reason"
date: 2009-09-24
forum: Desktop Environments
---

### Post by asdir on 2009-09-24
For some time now I have to kill trackerd and tracker-indexer after every boot. It seems that tracker tries to index forever, like it was in a kind of loop.
Is this problem known? I have not found a bug or a forum thread on this.
Is there any particular file type that would confuse tracker which I could look for in the indexed folder?

---

### Post by Giblet5 on 2009-09-24
Yes, that's why I turned it off. It indexes everything by default and I have terabytes of code, documents, etc.

Despite mounds and mounds of files, I have no need to search beyond the occasional find/grep.

It probably works well for a user with two email contacts, IMAP storage, and five Word documents.....and for people who learn how to use it effectively, which rules me out.

I disabled it from System/Preferences/Sessions.

You might begin with the man page for 'trackerd' to learn why it's doing that.

---

### Post by asdir on 2009-09-25
I don't think the problem is, that tracker has to cope with lots of data. Most of it was indexed a long tim e ago and that took only half a day or so.

But now it seems to be in some kind of loop. Has anything like that happened to someone else?

---

### Post by oldfred on 2009-09-25
When I first updated to 9.04 I had the same problem and turned tracker off and modified my Nvidia settings, so I was not sure what corrected my problem of cpu use near 100%.
I did some searching back then (May?) and there was an issue in tracker with large amounts of data and its database. They said the next update would have a new database and solve some of the problems.

---

