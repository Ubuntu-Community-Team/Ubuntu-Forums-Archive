---
title: "Empathy"
date: 2009-03-28
forum: General Help
---

### Post by PaulTR on 2009-03-28
Installed Empathy, but need backends to add accounts. I tried using the command given at [http://ubuntuforums.org/showthread.php?t=905889](http://ubuntuforums.org/showthread.php?t=905889) after adding that site to third party software list, but it gives me this message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtelepathy2 is already the newest version.
libtelepathy2 set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transmission: Depends: transmission-cli (>= 1.06-0ubuntu6) but it is not going to be installed
                Depends: transmission-common (= 1.06-0ubuntu6) but 1.22-1ubuntu1~hardy1 is to be installed
E: Broken packages


Anywho, any way I can get it up and running?

---

### Post by Xero Xenith on 2009-03-28
You have broken packages. Open Synaptic, go to *Edit - Fix Broken Packages*, then *Edit - Apply Marked Changes* - then retry.

-X

:)

---

