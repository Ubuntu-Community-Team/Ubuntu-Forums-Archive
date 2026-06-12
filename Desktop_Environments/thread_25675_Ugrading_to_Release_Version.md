---
title: "Ugrading to Release Version"
date: 2005-04-10
forum: Desktop Environments
---

### Post by rbowen on 2005-04-10
Greetings,

Just wondered if it is possible to upgrade to release version of hoary without a total rebuild. I'm currently on pre-release

Regards
RB

---

### Post by kkathman on 2005-04-10
Yep, you should just make sure your repositories are correct in /etc/apt/sources.list, which they should be.  Then simply do:

sudo apt-get update

and

sudo apt-get dist-upgrade


Hope this helps.

---

### Post by Jonathan2007 on 2005-04-10
I believe you would just use apt-get update and then apt-get dist-upgrade.

Oops yeah I forgot the sudo and I got beat.  :-)

---

