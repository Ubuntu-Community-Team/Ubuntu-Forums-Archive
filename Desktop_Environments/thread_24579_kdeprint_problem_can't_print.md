---
title: "kdeprint problem: can't print"
date: 2005-04-07
forum: Desktop Environments
---

### Post by freelsjd on 2005-04-07
Within firefox, click .pdf, open up acroread within firefox, view .pdf fine

Click print, opens up print dialog box, application says "kprinter", system has
a functional cups underlying.

Click OK under kprinter, get error message dialog box

Last message to the screen is

"A print error occurred. Error message received from system:

Unable to start child print process. The KDE print server (kdeprintd) could not be contacted. Check that this server is running."

There is no kdeprintd running.  I have this file out of the kdelibs4 package 
which is the only reference to kdeprintd on the system

dpkg -S /usr/lib/kde3/kded_kdeprintd.so

So, what is missing/wrong with the system (up-to-date hoary system)

---

### Post by freelsjd on 2005-04-07
Is no one else having this problem ?  If not, perhaps there is an issue with the kubuntu install  (actually the kubuntu-desktop) ?

---

### Post by DonVla on 2005-06-01
hallo,

instead of using the "lp/lpr" command, use "kprinter --stdin". then it should work.
hope this helps...

---

