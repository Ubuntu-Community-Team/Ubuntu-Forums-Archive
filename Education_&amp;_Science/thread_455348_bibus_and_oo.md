---
title: "bibus and oo"
date: 2007-05-26
forum: Education &amp; Science
---

### Post by code-breaker on 2007-05-26
I am using Kubuntu 7.04, with the default installation of oo (2.2.0). I installed bibus, and it runs fine using sqlite. However, when I select 'First Connection Wizard', and then click the 'Activate' button to activate oo's listening mode, oo begins to load, then crashes, and reloads, displaying the document recovery window, the document to be recovered is displayed as 'UnoConnectionListener (read-only)'. I suspect that this has something to do with pyuno, but I can't find enough info to figure out what to do next. 

Interestingly, oo displays the same behavior (immediately crashes, then restarts, showing the document recovery window), when within oo I select Tools/Bibliography Database. 

Any ideas?

---

### Post by tweedledee on 2007-05-26
> **code-breaker said:**
> I am using Kubuntu 7.04, with the default installation of oo (2.2.0). I installed bibus, and it runs fine using sqlite. However, when I select 'First Connection Wizard', and then click the 'Activate' button to activate oo's listening mode, oo begins to load, then crashes, and reloads, displaying the document recovery window, the document to be recovered is displayed as 'UnoConnectionListener (read-only)'. I suspect that this has something to do with pyuno, but I can't find enough info to figure out what to do next. 

Interestingly, oo displays the same behavior (immediately crashes, then restarts, showing the document recovery window), when within oo I select Tools/Bibliography Database. 

Any ideas?

Reinstall the openoffice packages?

---

### Post by code-breaker on 2007-06-24
I *finally* got this working. Here's the story, in case someone else has the same problem.

I remember reading somewhere that pyuno was not working properly, and that there were two different versions. Tonight, I happened to be scrolling through my list of apps in synaptic, and saw the package 'openoffice-pyuno' which was unchecked. I did a search for 'pyuno', and It found that package, and python-uno, which was installed. A-ha! I tried uninstalling python-uno, but (and this is crazy), synaptic then said it had to uninstall a bunch of packages (some associated with Mozilla Thunderbird!?), and worse, *install* a bunch too. This is crazy. So, I try installing the other pyuno package (openoffice-pyuno), and it wouldn't let me, saying this package depends on openoffice-org, and python2.3, niether of which could be installed. Again, crazy. 

I thought maybe I'd install version 2.2.1 of oo, (kubuntu has 2.2.0 installed), but this seemed like a major headache. I did some searching online, and found the following page:

[http://rpmfind.net/linux/rpm2html/search.php?query=openoffice.org-pyuno](http://rpmfind.net/linux/rpm2html/search.php?query=openoffice.org-pyuno)

...which contains a download link for openoffice.org-pyuno version 2.2.0. Hmm. I downloaded the rpm, tried installing via alien, and it worked! Bibus now talks to oowriter! Freakin' weeks of struggling with this!

---

### Post by UI-Freak on 2007-06-24
Didn't help here. I give up, just like these guys:

[http://sourceforge.net/forum/forum.php?thread_id=1463866&forum_id=380178](http://sourceforge.net/forum/forum.php?thread_id=1463866&forum_id=380178)

---

