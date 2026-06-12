---
title: "Installing UFO alien invasion"
date: 2007-01-03
forum: Gaming &amp; Leisure
---

### Post by luvinit on 2007-01-03
Hi I am trying to install the RC6 version of UFO, there is only a tar version of it, by the looks of things.  The following instructions 

[http://ufo.myexp.de/phpBB2/viewtopic.php?t=797](http://ufo.myexp.de/phpBB2/viewtopic.php?t=797)

don't work, they fail at "make src", the error message being "no rule to make target". Any ideas? Thanks.

---

### Post by dorcssa on 2007-01-03
Do you have build-essential installed? Without that, you cannot install from source.

See this page: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by luvinit on 2007-01-03
the build-essential box is checked in synaptic so I assume that means it is installed.

---

### Post by luvinit on 2007-01-04
I wasn't able to get to the bottom of the problem but the following method works, but takes literally all day to compile

[http://ufo.myexp.de/wiki/index.php/Debian](http://ufo.myexp.de/wiki/index.php/Debian)

Watch out for usual problems like not having the correct repositories installed. The bit where it talks about the path command is confusing so you are probably better off ignoring it.

---

