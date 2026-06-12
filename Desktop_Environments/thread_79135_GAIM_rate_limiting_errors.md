---
title: "GAIM rate limiting errors"
date: 2005-10-19
forum: Desktop Environments
---

### Post by Strife on 2005-10-19
So it appears that recently AIM has done something to reduce the rate limit for IMs. This means that since GAIM autochecks away messages, I get rate limiting errors as soon as I login, so if I try to talk to someone, they can't see what I wrote (and there's no way of knowing whether or not someone got the message).

I've looked all over, but I can't find an option to disable auto-away checking. Am I missing it, or does it really not exist? If not, I'll go ahead and file a bug report with GAIM.

---

### Post by hunteramor on 2005-10-19
i've been getting the same error, but it started immediately after i upgraded to breezy.  i think breezy included a change in version for Gaim, so my guess is this version of Gaim is auto-checking too often.  anyone know for sure what the deal is here?

---

### Post by unclben on 2005-10-19
I've been getting the same error in both Breezy (shipping build) and WinXP (gaim 1.5.0).

---

### Post by Strife on 2005-10-19
I should've checked the bugs list first, because they're aware of the problem. For reference, the bug is listed here: [http://sourceforge.net/tracker/index.php?func=detail&aid=1326766&group_id=235&atid=100235](http://sourceforge.net/tracker/index.php?func=detail&aid=1326766&group_id=235&atid=100235)

I made the suggestion of adding an option, though supposedly it's been fixed in CVS.

---

