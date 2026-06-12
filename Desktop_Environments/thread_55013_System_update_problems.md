---
title: "System update problems"
date: 2005-08-07
forum: Desktop Environments
---

### Post by coolclassic on 2005-08-07
Just done a update and after some time kynaptic seemed to have froze so I closed down and found that the configuration had failed to finnish. So I did - sudo dpkg --configure -a - and found that I was unable to connect to one resource sight the connection kept failing.
 How can I omit this sight so I can complete the configuration.

---

### Post by jimbob on 2005-08-07
I have had a lot of problems using the us.archives for Ubuntu, including md5sum mismatches, etc.

  Try going through your /etc/apt/sources.list and changing everything from "us.archive..." to just "archive..." and run your update again.

---

