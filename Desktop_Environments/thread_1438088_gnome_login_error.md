---
title: "gnome login error"
date: 2010-03-24
forum: Desktop Environments
---

### Post by hollowhead on 2010-03-24
My wife cannot log in using gnome form GDM a window appears on an otherwise blank screen saying that an error occurred whilst loading or saving configuration information for update notifier.  More info appears Failed to contact configuration server... I can log in OK and so can my children.  What's going on and how do we repair it?  Ta. ubuntu 9.04

---

### Post by hollowhead on 2010-03-24
Solved-for anyone who has this problem I uninstalled gnome power manager which seemed to come up in the error messages and reinstalled it.  I installed another wm or two and logged in as my wife using afterstep went into gconf also at the heart of some of the error messages.  Made one or two random changes and saved them.  Deleted the .gconfd/savedstate file.  One of these things did it.  Suppose it was a corrupted file, the hd checks out ok using smartmontools.  :D

---

