---
title: "Wine in Kubuntu Dapper"
date: 2006-06-04
forum: Desktop Environments
---

### Post by jacksaff on 2006-06-04
I can't get BabasChess to run in wine in kubuntu dapper. The .msi file installed fine and all the files have shown up in the correct place but any attempt to run the exe results in a terminal-full of hex that I can't even begin to read, let alone trouble-shoot. I've previously had the same downloaded file install fine in dapper-based mepis with a slightly older version of wine. Might there be permission issues here? Dapper seems to have a lot of different defaults for permissions than mepis. 
Anyone else having trouble with wine in dapper? I know a lot of new stuff has landed in wine of late. Maybe a couple of regressions but it takes a while for all the bugs to get registered by search engines if you don't already follow the relevant threads.
Cheers,
JS

---

### Post by jamyskis on 2006-06-04
Are you using Ubuntu's own repository for WINE or have you been adding the "official" WINE ones? The ones found at winehq.org are more up to date. If you add ```
deb http://wine.budgetdedicated.com/apt dapper main
``` to your /etc/sources.list or through Synaptic that might help, if not now, then certainly later.

That said, I don't know which version of WINE is currently being used in Dapper, because I already had the repos in there. I would suspect the Dapper default is 0.9.13 though while the release containing all the bugfixes from Google is 0.9.14. Try it - it rocks.

---

### Post by jacksaff on 2006-06-04
9.14 from the repo you mentioned.

---

### Post by frying_fish on 2006-06-04
Well, the dapper default is 0.9.9 I think, looking in synaptic, but using wine's built package I have 0.9.14 as well.

---

### Post by jacksaff on 2006-06-04
Got it working. Must be something to do with permissions. I had to install wine, run winecfg and install the .msi files all as root and then create other folders for app data that my account has write permission for. Don't really see why wine should require root to install software. It's never had to in mepis or debian. Is this an ubuntu/sudo issue or have I just found a hard solution to an easy problem?

---

### Post by homersbrain on 2006-06-05
9.14 worked on breezy, but now it won't work on dapper with photoshop. Just loads until "Fetching Tools". Any ideas? Also IE4Linux doesn't work anymore either on a fresh dapper install.

---

### Post by darshanarc on 2008-06-29
meka mach:lolflag::guitar:an wada karanne na ne banzzz...mokada karanne?:confused:

---

