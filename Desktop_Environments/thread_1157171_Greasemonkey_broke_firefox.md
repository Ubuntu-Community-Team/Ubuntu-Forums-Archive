---
title: "Greasemonkey broke firefox"
date: 2009-05-12
forum: Desktop Environments
---

### Post by SilvaRizla on 2009-05-12
I have installed greasemonkey via the web as I was unaware that it is carried in the repo's and now firefox refuses to start.  When the icon is clicked the firefox window displays on the taskbar for a few seconds and then disappears.  If I run it through terminal I get this:

dave@desktop:~$ firefox
dave@desktop:~$


Which doesn't seem much to go on, and I am unable to uninstall via the package manager or sudo apt-get remove in terminal as this causes the system to hang.  I can't remove Greasemonkey through a package manager as it doesn't appear because the install source was different.

Any Ideas?

---

### Post by SilvaRizla on 2009-05-12
Seems firefox has a safe mode where you can select to disable all addons:

me@desktop: firefox -safe-mode

sorted

---

