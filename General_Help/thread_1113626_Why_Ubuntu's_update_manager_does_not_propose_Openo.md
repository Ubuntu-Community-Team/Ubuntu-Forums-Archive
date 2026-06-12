---
title: "Why Ubuntu's update manager does not propose Openoffice 3.0"
date: 2009-04-01
forum: General Help
---

### Post by egabrum on 2009-04-01
Why is that?
OO 3 has been out for a while now.
Should Ubuntu propose automatically the latest version of all the software installed?

This is mostly for my understanding of how the updates work in Ubuntu.

---

### Post by Excedio on 2009-04-01
I am all for Ubuntu doing this. It would have made my life easier when I wanted to upgrade to OOo 3.0
 
Not that downloading it and compiling it was terribly hard, but it would have saved me a lot of google searching if it was readily available.

---

### Post by Cheesehead on 2009-04-01
OpenOffice 3.0.1 is included in Jaunty (Ubuntu 9.04), which is scheduled to be released in late April.

For older releases (such as Intrepid 8.10), there are generally three flavors of updates:
- Security Updates. A new release of OO isn't a vulnerability fix, so won't be in among these.
- Bug Fix (aka Stable Release Update or SRU). A new release of OO isn't a bug fix, so won't be in among these.
- Backport. If you have the 'backports' repository enabled, the same version of OpenOffice in 9.04 will be tested by a team of volunteers to see if it works with older releases. If it does, it will be offered to older releases as a backport. For more information on backports, see [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

You can add OO3 today pretty easily from a PPA, other third-party repository, or by compiling it yourself, but that is beyond the scope of your question.

Ubuntu uses a six-month snapshot of upstream releases, not a rolling update, to balance the demand for the latest versions against the finite testing resources available and your system's stability. OO3 was released barely too late for the last snapshot. There was a lot of debate about that, and system stability won the debate.

---

### Post by sekinto on 2009-04-01
This is what I have in my /etc/apt/sources.list file:

```
##OpenOffice.org [latest]
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
```

The key I added is [here]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x60D11217247D1CFF").
[B]
[Instructions]("https://launchpad.net/~openoffice-pkgs/+archive/ppa")[/B]

---

### Post by Excedio on 2009-04-01
> **Cheesehead said:**
> Ubuntu uses a six-month snapshot of upstream releases, not a rolling update, to balance the demand for the latest versions against the finite testing resources available and your system's stability. OO3 was released barely too late for the last snapshot. There was a lot of debate about that, and system stability won the debate.
 
 
This part I can understand. Apology accepted. :D

---

### Post by ramjet_1953 on 2009-04-01
Follow these instructions and all should go well:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Regards,
Roger :cool:

PS If you are using 8.04 there are also links for that.

---

### Post by egabrum on 2009-04-02
Thanks guys.

---

