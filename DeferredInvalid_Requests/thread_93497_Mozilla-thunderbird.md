---
title: "Mozilla-thunderbird"
date: 2005-11-22
forum: Deferred/Invalid Requests
---

### Post by jamesc on 2005-11-22
The version of mozilla-thunderbird I seem to have is 1.0.7, but [http://www.mozilla.org/](http://www.mozilla.org/) now seems to be suggesting that people download 1.5RC3 (as it is listed as 'Other Mozilla Software' on mozilla's main page).

How stable is 1.5RC3?  Would it cause lots of problems to backport it?  Has some nifty features. :) 


-jamesc

---

### Post by veloct on 2005-11-22
thunderbird is at RC1, firefox is at RC3.  I use both right now without any issues.

---

### Post by jamesc on 2005-11-22
Apologies, typo.  You are right 1.5RC1.  

But still would like to start using it. ;-)

---

### Post by macleod199 on 2005-11-22
Won't be backported till it's in Dapper, which it's not. We just got a Firefox RC, finally.

On the downside apparently the release of Firefox RC3 (and probably final) has sucked up all the resources, so there won't be a new Thunderbird RC till maybe december (according to the head developer).

---

### Post by jdong on 2005-11-22
[QUOTE=jamesc]The version of mozilla-thunderbird I seem to have is 1.0.7, but [http://www.mozilla.org/](http://www.mozilla.org/) now seems to be suggesting that people download 1.5RC3 (as it is listed as 'Other Mozilla Software' on mozilla's main page).

How stable is 1.5RC3?  Would it cause lots of problems to backport it?  Has some nifty features. :) 


-jamesc[/QUOTE]

jdong@shuttle:~$ ubp mozilla-thunderbird
mozilla-thunderbird |    1.0.7-3 |      unstable | source, i386
mozilla-thunderbird | 1.0.7-0ubuntu1 |        breezy | source, i386
mozilla-thunderbird | 1.0.7-0ubuntu05.10 | breezy-updates | source, i386
mozilla-thunderbird | 1.0.7-0ubuntu1 |        dapper | source, i386

No newer thunderbird....


Firefox 1.5 RC2 is in Dapper, though of a very low quality (breaks Epiphany and locale packages, etc etc) though it builds fine. You can try using ubp-build.py to do it, and it'll work, though right now it's DEFINITELY not backports material, and probably won't be for another week or two or three.

---

