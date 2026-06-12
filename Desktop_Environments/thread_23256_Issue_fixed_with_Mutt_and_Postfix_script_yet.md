---
title: "Issue fixed with Mutt and Postfix script yet?"
date: 2005-04-01
forum: Desktop Environments
---

### Post by vvu on 2005-04-01
I downloaded Kubuntu Hoary 5.04 Preview two weeks ago after intial release and have been very pleased...new Linux/Kubuntu convert here.  

The issue I had was related to the DEFAULT software installation and apt-get/synaptic/kynapic issue with certain softwares installed by default - namely Mutt and Postfix causing some issues.  Again, out of 4 installations on 4 different machines, the systems complained about POSTFIX and MUTT being incorrectly installed or configured, but I never installed these components thus it was part of the DEFAULT installation.

Has this been fixed in the RC or will it be fixed by FINAL release?   [-o<   Anyone know?

---

### Post by vvu on 2005-04-05
Can anyone confirm this issue and whether it has been corrected?  Thanks.

---

### Post by bosteen on 2005-04-05
I for one can confirm the mutt-postfix snafu, and I have seen one of two others with the same problems.

As to whether it's fixed at the moment.... no idea, but I'll be trying another kubuntu install from a kubuntu-only disc soon. (ie no apt-get kde-desktop etc.) I'll post when that happens.

Ben

[Edit: Might as well put what fixed it for me here...
[] $ sudo /etc/init.d/postfix stop
[] $ sudo apt-get install postfix

/Edit]

---

### Post by vvu on 2005-04-05
FYI...I received these errors using the Hoary Kubuntu CD download - the PREVIEW release.  I did a few apt-get using Kynaptic and synaptic (just to update the system), but synaptic was the one to show me that there were errors primarily with the Mutt and Postfix packages.

Also, problem with KDE - when you open it as regular user and you try to open a component with Admin option - it either crashes or doesn't even show you the admin option (the settings do not become enabled).

I hope these things will be fixed before the final release - I think these things are simplistic in terms of QA and identification - why???  Cause I am a COMPLETE NEWBIE to Linux (2 - 2.5 weeks)!  and I found them.

---

