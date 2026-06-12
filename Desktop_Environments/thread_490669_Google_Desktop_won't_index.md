---
title: "Google Desktop won't index"
date: 2007-07-02
forum: Desktop Environments
---

### Post by shoofy on 2007-07-02
I installed Google Desktop for Linux 2 days ago and I've left my computer on ever since. Much of that time is what should have been "idle time" that GDS uses for indexing. However, 2 days later, my index status page claims that it has indexed a whopping 37 files (the same as it was 24 hours ago).

I've already tried stopping as many processes as possible, but still no luck. I've posted in the GDS for linux Google Group and the only answers I got were a couple other people with similar problems.

Has anyone here figured enough out about GDS for Linux in the last ~5 days since it came out to be able to help me?

---

### Post by gtr225 on 2007-07-02
I have the same exact problem. It indexed all my gmail but only a few files from my home directory and has yet to index all the other files i have on seperate hard drives. It still says: One-time index update in progress.
0.1% complete with about 5.8 idle hours left.

---

### Post by shoofy on 2007-07-02
I have the same 0.1% with 5.8 idle hours left. Seems to be the default starting point.

---

### Post by gtr225 on 2007-07-02
Did you add custom folders for Google Desktop to index (trying to see if our setups have anything in common)?

---

### Post by shoofy on 2007-07-03
yes I did. It's on a mounted drive too, if that matters. It has all my documents on it, so if GDS can't index it, it's pretty worthless to me.

---

### Post by gtr225 on 2007-07-03
Yea I have two other hard drives with all my multimedia on it and also a custom folder for my torrents and it has yet to index anything from them. I also have BOINC running all the time. I'm having second thoughts about GDL and I've already reinstalled beagle for the meantime.

---

### Post by vampireking on 2008-01-12
Try open your mail program and google desktop index your mails.
Then restart google desktop.
Mine works!

---

### Post by shoofy on 2008-01-12
I actually solved this problem a long time ago. Turns out I had a corrupt directory within what GDS was trying to index and it was choking on it. Works fine now.

---

