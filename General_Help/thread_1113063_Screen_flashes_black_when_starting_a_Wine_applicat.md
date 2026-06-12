---
title: "Screen flashes black when starting a Wine application"
date: 2009-04-01
forum: General Help
---

### Post by snivek on 2009-04-01
Whenever I start a Wine application my entire screen goes black for a couple of seconds and then comes back normally.  It also started flashing black whenever save a file using Word in Wine.  Running compiz or metacity does not seem to change anything.

Ubuntu 8.10
Wine-1.1.17
Intel GMA945

---

### Post by jackflap on 2009-04-01
> **snivek said:**
> Whenever I start a Wine application my entire screen goes black for a couple of seconds and then comes back normally.  It also started flashing black whenever save a file using Word in Wine.  Running compiz or metacity does not seem to change anything.

Ubuntu 8.10
Wine-1.1.17
Intel GMA945

Sounds like it could be the same issues that the Ubuntu devs are working to fix in Jaunty right now:

[https://lists.ubuntu.com/archives/ubuntu-devel/2009-April/027988.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-April/027988.html)

If you're up for testing Jaunty that'd be great. Otherwise, chances are it'll be sorted when Jaunty is released (in 22 days) anyway.

Alex

---

### Post by snivek on 2009-04-01
Great!  I am not opposed to moving to Jaunty.  My only question (sorry for straying off topic) is if when Jaunty is released will I simply be able to update to the full release from the beta builds or will I have to reinstall?

---

### Post by jackflap on 2009-04-01
> **snivek said:**
> Great!  I am not opposed to moving to Jaunty.  My only question (sorry for straying off topic) is if when Jaunty is released will I simply be able to update to the full release from the beta builds or will I have to reinstall?

You will automatically be upgraded to the latest final release just by installing updates (while on jaunty beta, in order to upgrade to jaunty you need to either install it from scratch or do a dist-upgrade in intrepid).

Please note though, that the package that is mentioned in the thread above hasn't been uploaded to jaunty yet, so you probably won't see an improvement until the testing is complete and it is committed (at which point you will receive it in the Jaunty updates).

---

