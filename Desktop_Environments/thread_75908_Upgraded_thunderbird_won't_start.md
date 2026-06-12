---
title: "Upgraded thunderbird won't start"
date: 2005-10-14
forum: Desktop Environments
---

### Post by sargonx on 2005-10-14
Hey there. I'm a Linux-Ubuntu newbie, with breezy preview installed a couple of weeks ago. I was happily using my mozilla thunderbird, it had recognized my previous profile and stored emails. On tuesday, I ran synaptic and it upgraded Thunderbird to 1.0.7. Since then, I've been unable to run it.

When I click on the panel icon or the menu icon, nothing happens. If I type mozilla-thunderbird into the terminal, nothing happens (it is like I typed enter). If I type sudo mozilla-thunderbird (and here it gets interesting), I get "selected locale: en-US
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 159: 11630 Segmentation fault      "$prog" ${1+"$@"}".

It is almost certain that the new version is screwing me. I've installed, uninstalled and completely reinstalled it several times over, nothing happens. I tried to run the executable from /usr/bin/mozilla-thunderbird, nothing will happen there. Any hints?

Thanks in advance

---

### Post by sargonx on 2005-10-24
Update: as of today, a new version of thunderbird was put into the repository. I upgraded it and the problem was solved. Long live Ubuntu!

---

