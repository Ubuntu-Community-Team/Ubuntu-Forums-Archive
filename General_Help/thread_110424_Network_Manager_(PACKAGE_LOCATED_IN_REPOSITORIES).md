---
title: "Network Manager (PACKAGE LOCATED IN REPOSITORIES)"
date: 2005-12-30
forum: General Help
---

### Post by jrattner on 2005-12-30
The Network manager package in the repositories is great.  It is the best Networking tool I have ever seen in linux.  The only draw back is that it occasionally gives me errors in gnome.  But besides that, it functions perfectly.

  I was wondering if anyone knows when the build 0.4.1 will be upgraded to the newest release of network manager (0.5.1).

---

### Post by sciurus on 2005-12-31
Not until Dapper Drake, I'm sure, unless a security flaw is discovered in 0.4.1 which can't be fixed otherwise.

---

### Post by Confuse on 2005-12-31
[http://bootlab.org/~j/NetworkManager-breezy/](http://bootlab.org/~j/NetworkManager-breezy/)

There is an unoficial repository, it works fine with me.

---

### Post by jdong on 2005-12-31
We (Backports project) looked at this as a backports candidate, but determined that later versions are largely unuseful for stable Ubuntu releases unless a good chunk of the core system (HAL, etc) are also updated (which is not an option).


Dapper is going to have great Network Manager integration.

---

### Post by jdong on 2005-12-31
Also, I do not like the way the packages in the above repositories were done. It needs some sort of version tag (i.e. breezy0, ~breezy0) to distinguish it from Dapper packages by the identical version, or when you try to upgrade to Dapper you're going to hate yourself for installing stuff from that repository.

---

