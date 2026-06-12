---
title: "Logout Problem"
date: 2005-10-18
forum: Desktop Environments
---

### Post by shekhark on 2005-10-18
I have been experiencing a strange (and highly annoying) problem with logging out of sessions in Ubuntu wherein when one selects System --> Logout and rather than logging out, restarting or shutting down according to what is selected, the session gets saved (dialogue box confirms) and nothing else happens. If I select System --> Logout a second time after the session gets saved, then my system does what I tell it, but never the first time. I've experienced this problem in 5.04 (Hoary) and 5.1 (Breezy Preview), and am totally stumped on how to fix it, having sought out help on irc and other forums, re-installed gnome-session, tinkered with metacity, tried every possible combination of settings in the sessions prefs, etc. Please someone let me know how I can get around or fix this annoying problem.

---

### Post by aysiu on 2005-10-19
Have you tried just shutting down from terminal? ```
sudo shutdown -h now
```

---

### Post by mvandeg on 2005-10-22
I have exactly the same problem. Changing settings doesn't seem to help.

---

### Post by shekhark on 2005-10-22
Yes I have had this problem both with Hoary and throughout the development version and official release of Breezy. I have heard reports of others who had this, and then it "just went away", which it hasn't for me. It seems that Breezy is plagued with several such problems related to GNOME Display Manager, gksudo, etc. I hope someone in the community can address this issue.

---

