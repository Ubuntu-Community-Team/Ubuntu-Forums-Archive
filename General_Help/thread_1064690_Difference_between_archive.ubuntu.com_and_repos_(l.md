---
title: "Difference between archive.ubuntu.com and repos? (libunwind)"
date: 2009-02-09
forum: General Help
---

### Post by yang on 2009-02-09
The libunwind package seems to exist here:

[http://archive.ubuntu.com/ubuntu/pool/main/libu/libunwind/libunwind_0.98.5-8build1.dsc](http://archive.ubuntu.com/ubuntu/pool/main/libu/libunwind/libunwind_0.98.5-8build1.dsc)

'aptitude search libunwind' returns nothing - is this because the package is on archive.ubuntu.com?  Is it possible to install libunwind through apt?  Is it recommended?  Why did this get moved to archive.ubuntu.com?  Thanks in advance for any answers.

---

### Post by Sam Lars on 2009-02-09
When I look in that directory on us.archive.ubuntu.com, it has all of the accompanying files, but there are no packages in there.
I think that that site is same as the default repository for Ubuntu.  You could also look in Synaptic to see if you can find anything.

---

### Post by HyRax on 2009-02-09
All mirrors should be identical. If your local mirror is missing files then it is either incomplete (not updated often or at all) or it is being updated right this very minute with new data that hasn't yet appeared on your local mirror (ie: empty directories, but not for too long - RSync creates the entire required directory tree before mirroring the data that is supposed to occupy those directories).

---

