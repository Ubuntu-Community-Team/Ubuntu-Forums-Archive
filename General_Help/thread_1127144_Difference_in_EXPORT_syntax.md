---
title: "Difference in EXPORT syntax"
date: 2009-04-16
forum: General Help
---

### Post by PACSFerret on 2009-04-16
Installing Aptana IDE onto Intrepid, and discovered an interesting thing.

The background is this - Aptana depends on a version of xulrunner not included in FF3.  The solution is to install xulrunner seperately and set the environment variable MOZILLA_FIVE_HOME accordingly.  

While

MOZILLA_FIVE_HOME=/usr/lib/xulrunner
export MOZILLA_FIVE_HOME
/path/to/aptana/binary

works,

export MOZILLA_FIVE_HOME=/usr/lib/xulrunner
/path/to/aptana/binary

doesn't

In both cases, the export table looks exactly the same but there has to be some difference between the two.?????

---

