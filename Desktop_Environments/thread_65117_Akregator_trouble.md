---
title: "Akregator trouble"
date: 2005-09-13
forum: Desktop Environments
---

### Post by f1dave on 2005-09-13
Hey all,

I've been a happy user of this fantastic kde rss reader up until two days ago, when it crashed with this error:

The standard feed list is corrupted (invalid XML). A backup was created:
/home/meacod01/.kde/share/apps/akregator/data//feeds.opml-backup.1126595389

Then it simply dies with a segfault. Now I've looked at the aforementioned file, restored it to simply feeds.opml and the same thing happens. If anyone's got any ideas on how to fix this, please tell me so I can read my articles once more! :)

---

### Post by lippel on 2005-09-13
[QUOTE=f1dave]Hey all,

I've been a happy user of this fantastic kde rss reader up until two days ago, when it crashed with this error:

The standard feed list is corrupted (invalid XML). A backup was created:
/home/meacod01/.kde/share/apps/akregator/data//feeds.opml-backup.1126595389

Then it simply dies with a segfault. Now I've looked at the aforementioned file, restored it to simply feeds.opml and the same thing happens. If anyone's got any ideas on how to fix this, please tell me so I can read my articles once more! :)[/QUOTE]

Check if there is a valid backup of feeds.opml (invalid ones have most likely a size of 0 bytes). If not, check if you have a manual backup... If not, your feed list is lost :-/ You should delete feeds.opml then and restart Akregator to get a working Akregator, with the default feed list (Which reminds me that we should handle these problems better in the next release).

---

### Post by f1dave on 2005-09-14
Heh, thanks for that. A blank list it is :S

---

### Post by kkass on 2007-03-21
Thanks!  This fix seems to work for other Akregator segfaults as well.  (It was crashing for me periodically while fetching feeds and always when exiting,)

---

