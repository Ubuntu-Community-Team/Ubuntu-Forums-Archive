---
title: "Repository for xfig 3.2.4?"
date: 2005-12-30
forum: General Help
---

### Post by bigblop on 2005-12-30
I have tried to use the new xfig 3.2.5 alpha but I cannot open .fig files that I made with 3.2.4. Is there someway to add a repository that contains the old version?

---

### Post by astoltz on 2005-12-30
Is it in the Hoary repo's?  Just add ```
deb http://us.archive.ubuntu.com/ubuntu hoary universe main restricted multiverse
``` to your /etc/apt/sources.list

---

### Post by bigblop on 2005-12-30
I have now added that to my sources.list but I can still only get 3.2.5 alpha!

Is the old version completely removed?

---

### Post by hajk on 2005-12-30
Any idea why you can't open old .fig files in Xfig 3.2.5? My experience is a different one: I find that I can open all my old .fig files going back 10 years or so. Have you filed a bug with Ubuntu or at [www.xfig.org?](www.xfig.org?) Have you looked for similar bugs? Reverting to an old version of Xfig seems like a drastic measure to me... (just my 2 Eurocents worth:p )

---

### Post by astoltz on 2005-12-30
[QUOTE=bigblop]I have now added that to my sources.list but I can still only get 3.2.5 alpha![/QUOTE]

I don't know for sure what version is in Hoary.  But in synaptic, search for 'xfig', then from the package menu, select 'force version'.  You should be able to select which version gets installed (if there's something besides 3.2.4).

Oh yeah, you did a sudo apt-get update, correct?

---

