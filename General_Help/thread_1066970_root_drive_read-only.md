---
title: "root drive read-only"
date: 2009-02-11
forum: General Help
---

### Post by tivey on 2009-02-11
Hi, problem on boot where it can't load the gui because it says the root drive is mounted in read only mode. Also when doing a routine disk check it sometimes throws an error about half way through complaining again that the root drive is in read-only mode. You can sometimes fix this by doing a fsck and fixing a load of broken ??innodes?? but however, this doesn't always work. I've tried re-installing a few times using 8.04 and 8.10 but the same problems persist. I haven't re-formated the drive on any re-installation so I'd guess that the partition could be messed up. As i was writing this the root drive decided to go into read-only mode and it all crashed. Now the grub won't even load (I'm on the live disk)?? Any help would be really useful, I'm fairly new to Linux (only been using it for a few months).

---

### Post by jman6495 on 2009-02-13
hi

first of all i'm really sorry about your problems , it's difficult for new users when you get these errors , i personally can't help you bit if you use the search function you will find other people with the same problem and hopefully a solution .

Also , did you modify any file permissions recently?

Hope this helps
   jman6495

---

### Post by Old *ix Geek on 2009-02-13
From what you're describing it sounds like it could be a hard drive problem, as in a hard drive getting ready to crash.  If I were you the first thing I'd do is make backups of important files!  Then you can make more efforts to resolve the problem, but it sounds like a new drive might be in order.

Something to keep in mind with Linux--as opposed to the evil dark side--is that reinstalling and reinstalling is just not the way it's done.  It's pretty unusual to need to reinstall Linux to fix problems, unlike windoze where people get used to reinstalling every few months when the system slows to a crawl and/or crashes all the time.

---

