---
title: "Ubuntu 14.04 and Cinnamon"
date: 2014-03-31
forum: Desktop Environments
---

### Post by tachum1 on 2014-03-31
I have been using Cinnamon on Ubuntu 13.10 (and previous versions) on my main laptop. 

I installed Ubuntu 14.04 on my spare laptop and it goes well but I can't see how to install Cinnamon on 14.04. I usually just put in the three command lines, but can't find how to do this for 14.04. Could it be that it currently too unstable? I've checked through the forum and can't see any other similar queries for 14.04. I even did a google search.

Thoughts??

GH

---

### Post by buzzingrobot on 2014-03-31
Cinnamon is in the 13.10 repos but is not in the 14.04 repos at this time.

---

### Post by grahammechanical on 2014-03-31
I see cinnamon 1.7.4-2ubuntu6 in the software centre of my trusty tahr. Are you sure that you have enabled all the repositories? I guess that something like cinnamon would be in the Universe repository.

Regards.

---

### Post by buzzingrobot on 2014-03-31
Hmmm. I searched at packages.ubuntu.com and got no results for "Cinnamon" in Trusty.  No results in Software Center here, either. Nemo's there, though.

---

### Post by Redalien0304 on 2014-03-31
just use Cinnamon Nightly Repo is what im using

---

### Post by bapoumba on 2014-04-01
Moved to Ubuntu +1.

---

### Post by lollerman69 on 2014-04-19
This is because of bug #1266336  ([https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1266336](https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1266336))  Cinnamon ~1.7 will break your startup menu so it was removed from the trusty repository until the bug is fixed.   .... However, Users report that with a bit of tinkering that Cinnamon ~2.0 works from the cinnamon nightly repo.

---

### Post by dawgfan16 on 2014-04-19
I can confirm that using the cinnamon nightly repo will get it installed and once installed, I have had no hiccups as of yet.

---

### Post by cariboo on 2014-04-19
Moved to Desktop Environments seeing as Trusty has been released.

---

