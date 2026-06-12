---
title: "Jauntu: 2 minute disk grounding after initial KMail check"
date: 2009-05-01
forum: Desktop Environments
---

### Post by mibadt on 2009-05-01
Hi,
I'm on a fresh installed Kubuntu Jaunty (with a separate /home partition migrated from ver 8.10).

Although all my KMail (ver 1.11.2 under KDE 4.2) folders  are fully compacted, I recently "suffer" from the following flamboyance:

1. Once I open (even after fresh boot) Kontact the system is (still) responsive as usual.
2. The moment I click (in KMail) check mail (I have 3 accounts and 3 identities), the hard drive begins to "work" furiously" (even when I have NO new mail messages in any account and no pending message in outbox) for about 2 minutes. During this period KMail is hardly responsive (with about 10 sec response time for mouse folder selections), although I can easily switch to other open applications which remain responsive. Running top at this time shows kontact using 30-50% of my CPU, yet NO swap used (I have 2 GB RAM), while all other processes behave "nice" (resource usage-wise). Once the disk stops grinding, kontact's CPU usages also declines to a normal 3-4% and stays there.

Any idea what's wrong, and how can I get a responsive KMail from start?

Thanks up front!

Regards,

Michael Badt

---

### Post by Zorael on 2009-05-01
Sounds like that sqlite thing present in current Quassel/older Firefoxes where it commits writes to the harddrive at every write, instead of caching them up and then writing in a batch.

Search [launchpad](http://bugs.launchpad.net/ubuntu), post a bug report if there isn't one already.

---

### Post by mibadt on 2009-05-02
Thanks, yet the grinding occurs BEFORE launching Firefox (the latest 3.08 version).

Michael Badt

---

### Post by rastafar on 2009-10-21
Hi, I have simmilar problem. As I start Kmail it starts to gargle my hdd and it took about 3 minutes. During this it is possible to use other apps almost normally, but Kmail response it very very poor, it took ages till it reacts to any click - not possible to use it. I have older P4 @ 3Ghz with 2GB RAM. I had this problem in hardy too, once I moved the .kde/share/apps/kmail into some other location, configured the kmail again and imported all messages back, it worked normally for some time. But then again the same problem. Update to newer distribution (JJ) did not solved this. I have no time to do the whole import again now... Maybe - just a guess - Im sometimes connecting to my computer from work via NX client (sth like RDP in windows) and sometimes I log in when Im loggen in on the computer also. NX is creating another instance of KDE, not just shadowing the monitor. Therefore there is a possibility that 2 kmails were rinning at same time and some of its configuration files become damaged and this is the cause of disk gargling. But it is just my guess... Maybe you can confirm it. But I want to fix this, it is very confusing..

I have also separate /home on separate drive

EDIT: I found solution, its quite easy and fast:

- open KMAIL, wait until it stop gaargling your HDD

- go trough all your mail folders, right-click each folder and select "rebuild index" from the right-click menu, confirm that you want to rebuild the index

- now close kmail and open it again, problem is solved, no HDD gargling anymore :-)

---

### Post by jwood1961 on 2009-11-16
I upgraded to Koala on a netbook and now have this same phenomenon - although the disk grinding and poor Kmail responsiveness goes on for more like 10-15 minutes. It's at every startup.

---

