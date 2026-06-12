---
title: "PHP Processes at 100%"
date: 2011-10-03
forum: Desktop Environments
---

### Post by craigp on 2011-10-03
I have the desktop version of Ubuntu on a server of mine that is running php/mysql. It has a number of cronjobs and some of them are not completing properly. Currently, I have 3 PHP processes between 95-100% and have been like that for awhile.

```

24326 root      20   0 21652 7280 4928 R   99  0.1 459:15.61 php
  646 root      20   0 21652 7276 4928 R   99  0.1   3334:22 php
11677 root      20   0 21652 7280 4928 R   98  0.1   1873:00 php

```

Any way of finding out which php files are being held up? any way of getting them to run through?

---

