---
title: "XGL problem"
date: 2006-07-08
forum: Desktop Environments
---

### Post by t_ras on 2006-07-08
install through this thread:  
[http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189)

I'm using ubuntu 6.06 on AMD 64


I can't install compiz because apt-get couldn't find libsvg 0.1.6 which was required.
I installed 0.1.5, but it doesnt seem to be enough...

any ideas? is XGL usable in AMD64 at all?

Thanks

---

### Post by t_ras on 2006-07-08
found the sulution in AMD64 forum

---

### Post by mock on 2006-07-09
I have searched amd64 forum and only got old sulotions with cvs compiled long ago (feb)
I've manged to track down  l.60 of libsvg (cairo). but i don'r know if i should compile it myself or wait till the repo manager decised the new version is sable enough to include in the repo.
(how ofter are the repos updated?)

---

### Post by RAOF on 2006-07-09
You should check out the [compiz.net](compiz.net) forums.  More specifically, were have you been trying to do?  What repositories have you been trying to install XGL/Compiz from?

All the **very** latest packages can be got from my repository (I'm the one building the AMD64 packages for Quinn) - [raof.dyndns.org/falcon](raof.dyndns.org/falcon).  The mirror on that page (moshen.de) is slightly (generally by less than a day) older than my raof.dyndns.org, plus has significantly better bandwidth.  Then the "official" Quinn/regamanu repositories are a bit behind moshen.de.

---

