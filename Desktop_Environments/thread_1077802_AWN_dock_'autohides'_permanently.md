---
title: "AWN dock 'autohides' permanently"
date: 2009-02-22
forum: Desktop Environments
---

### Post by pixnaps on 2009-02-22
Hi, I'm using Avant Window Navigator as a dock/launcher in Intrepid, but I've noticed that if I set it to 'autohide' (i.e. so that it only becomes visible if I shift the mouse to the bottom of the screen where the bar resides) after a while it hides <i>permanently</i>, i.e. it won't even appear if I go searching for it with my mouse.  (System Manager insists that the process is still 'sleeping' in the background, though.)  I then have to re-open AWN if I want it to be visible again.

For now I've just disabled autohide so it's always visible. But I would much prefer that the autohide feature actually work.

Any suggestions?

---

### Post by pixnaps on 2009-02-23
*bump*

---

### Post by moonbeam on 2009-02-23
Autohide is known to be buggy and has always been buggy.  see the autohide [bug list]("https://bugs.launchpad.net/awn/+bugs?field.searchtext=autohide&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=").

We will resolve this with the 0.4 rewrite that is in the works... till then the current implementation is inherently a hack.

---

